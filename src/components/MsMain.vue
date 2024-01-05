<template>
  <main>
    <form>
      <MsInput label="Largeur" :formValue="board.width" @update:formValue="v => board.width = v"/>
      <MsInput label="Hauteur" :formValue="board.height" @update:formValue="v => board.height = v"/>
      <MsInput label="Bombes" :formValue="board.bombs" @update:formValue="v => board.bombs = v"/>
      <MsSubmit value="Générer" @click.prevent="getBoard(this.board.width, this.board.height, this.board.bombs)"/>
    </form>
    <MsRow v-for="(r, i ) in this.board.map" :key="r" :id="'r' + i">
      <MsCase v-for="c in r" :key="c" :casePosition="c"> <span v-if="c.type=='digit'">{{ c.value }}</span><SvgBomb v-else-if="c.type=='bomb'"/> </MsCase>
    </MsRow>
  </main>
</template>

<script>
import MsInput from './form/MsInput';
import MsSubmit from './form/MsSubmit';
import MsCase from './MsMain/MsCase.vue';
import MsRow from './MsMain/MsRow.vue';
import SvgBomb from './svg/SvgBomb.vue';

export default {
  name: 'MsMain',
  components: {
    MsInput,
    MsSubmit,
    MsCase,
    MsRow,
    SvgBomb
  },
  data() {
    return {   
      test: 13, 
      board: {
        width: 16,
        height: 16,
        bombs: 40,
        map: []
      }
    }
  },
  methods:{
    getItem(row, column, value, type) {
      return {row, column, value, type}
    },
    updateDigit(target){
      target.type == "digit" ?
        target.value++ :
        target.type == "bomb" || (target.value = 1, target.type = "digit")
    },
    getRandomCoordinates(maxRow, maxColumn){
        return { row: Math.floor(Math.random() * maxRow), column: Math.floor(Math.random() * maxColumn) }
    },
    getBombsCoordinates(maxRow, maxColumn, amount) {
      const bombsCoordinates = [];

      for(let i = 0; i < amount; i++){
        let handler;
        do{
          handler = this.getRandomCoordinates(maxRow, maxColumn);
        }
        while(bombsCoordinates.includes(handler))

        bombsCoordinates.push(handler)
      }
     
      return bombsCoordinates
    },
    getArrays(width, height) {
      let board = [];

      for(let r = 0; r < width; r++){
        board.push(Array())
        for(let c = 0; c < height; c++){
          board[r].push(this.getItem(r, c, "", "plain"))
        }
      }

      return board;
    },
    getBoard(width, height, bombs){
      console.log(this.board.width)
      const bombsCoordinates = this.getBombsCoordinates(width, height, bombs)

      bombsCoordinates.push({row: 0, column: 0})
      bombsCoordinates.push({row: 0, column: 1})

      const board = this.getArrays(width, height)

      bombsCoordinates.forEach(b => {
        const {row, column} = b;
        board[row][column] = this.getItem(row, column, "", "bomb")

        const cases = [
          {row: row-1, column},
          {row: row+1, column},
          {row, column: column-1},
          {row, column: column+1},
          {row: row+1, column: column+1},
          {row: row+1, column: column-1},
          {row: row-1, column: column-1},
          {row: row-1, column: column+1}
        ]

          cases
          .filter((c) => c.row >= 0 && c.row < width && c.column >= 0 && c.column < height)
          .forEach((coordinates) => {
            this.updateDigit(board[coordinates.row][coordinates.column])
          })
      })

      this.board.map = board;
    }
  }
}
</script>

<style scoped>
  main{
    padding: 1em 4em
  }

  form{
    margin-bottom: 4em;
  }

</style>
