<template>
  <form>
    <label>Email</label>
    <!-- 类型为email，required 必填项 -->
    <!-- v-model 实现数据，用户表达填充双向绑定 -->
    <input type="email" required v-model="email" />
    <label>Password</label>
    <!-- 类型为email，required 必填项 -->
    <input type="password" required v-model="password" />
    <label>roel:</label>
    <!-- v-model绑定下拉列表框 -->
    <select v-model="roel">
      <option value="designer">网页设计师</option>
      <option value="enginner">前端工程师</option>
    </select>
    <div class="agrees">
      <input type="checkbox" v-model="agree" required />
      <label> 我同意 </label>
    </div>
    <label>Skill:</label>
    <input type="text" v-model="temSkill" @keyup.enter="getSkills" />
    <div class="skills" v-for="(skill, index) in skills" :key.alt="index">
      {{ skill }}
    </div>
  </form>
  <p>email:{{ email }}</p>
  <p>password:{{ password }}</p>
  <p>roel:{{ roel }}</p>
  <p>agree:{{ agree }}</p>
</template>
<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      // 设置初始值,option的value值
      roel: "designer",
      // 设置初始值,checkbox的checked值
      agree: false,
      skills: [],
      temSkill: "",
    };
  },
  methods: {
    // 获取输入框的值,按下“，”添加到数组中
    getSkills(e) {
      // 判断是否按下“，”并且输入框中有临时值
      if (this.temSkill) {
        //判断数组中是否已经包含该值，不能重复输入。includes():判断数组中是否包含某个值。如果包含返回true，否则返回false
        if (!this.skills.includes(this.temSkill)) {
          // 如果比包含该值，则用push():向数组中添加一个或多个元素，并返回新的长度。
          this.skills.push(this.temSkill);
        }
        // 清空输入框的临时值
        this.temSkill = "";
      }
    },
  },
};
</script>
<style scoped>
form {
  max-width: 450px;
  margin: 200px auto;
  padding: 40px;
  border-radius: 10px;
  background-color: #ffff;
  text-align: left;
}
label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.6em;
  /* 文本大写 */
  text-transform: uppercase;
  font-weight: 900;
  padding: 0 10px;
}
input,
select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  /* box-sizing: border-box;内容区的实际宽度是width减去(border + padding)的值 border-box不包含margin*/
  /* box-sizing:content-box;默认值 只包括内容的宽和高， 不包括边框（border），内边距（padding），外边距（margin）。
    注意: 内边距、边框和外边距都在这个盒子的外部*/
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ccc;
  color: #555;
}
input[type="checkbox"] {
  width: 30px;
  display: inline-block;
  /* 相对定位 */
  position: relative;
  top: 2px;
}
.skills {
  display: inline-block;
  padding: 5px 10px;
  margin: 20px 10px 0 0;
  color: #555;
  background: #ccc;
  font-size: 12px;
  font-weight: 900;
  border-radius: 20px;
  /* 鼠标悬停呈现手的样式 */
  cursor: pointer;
}
</style>