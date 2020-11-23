<template>
  <div>
    <h5>Covid Checking</h5>
    <div class="question-container">
      <div class="question" v-for="(item, index) in questionList" :key="index">
        <input
          type="checkbox"
          :id="item.question"
          :value="item.value"
          @click="clickQuestionHandler"
        />
        <label>{{ item.question }}</label>
      </div>
    </div>
    <button class="btn-submit" @click="clickSubmitHandler">Submit</button>
  </div>
</template>

<script>
import question from "@/assets/question";
export default {
  name: "HelloWorld",
  data() {
    return {
      questionList: question,
      score: 0,
      status: ""
    };
  },
  methods: {
    clickQuestionHandler(e) {
      if (e.target.checked) {
        this.score += parseInt(e.target.value);
      } else {
        this.score -= parseInt(e.target.value);
      }
      this.score = this.score < 0 ? 0 : this.score;
    },
    clickSubmitHandler() {
      if (this.score <= 1) this.status = "Very low risk";
      if (this.score >= 2 && this.score <= 4) this.status = "Medium risk";
      if (this.score >= 5) this.status = "High risk";
      alert(this.status);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.question-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  padding-left: 20%;
}

.btn-submit {
  margin-top: 1rem;
}
</style>
