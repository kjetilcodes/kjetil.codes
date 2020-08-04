<template>
  <Standard>
    <div class="container">
      <article id="intro">
        <h1>About me</h1>
        <ul>
          <li v-for="(prop, key) in intro" :key="key" class="intro-li-item">
            <span class="about-key">{{key}}:</span>
            <span class="about-prop">{{prop}}</span>
          </li>
        </ul>
        <p>I have been learning web-development over the course of a few years. I'm increasingly looking to the security and privacy aspect of the web.</p>
      </article>
      <article>
        <h1>Skills</h1>
        <ul class="skill-box">
          <li
            v-for="(prop, key) in skills"
            :key="key"
            class="skill-li-item"
            :class="key"
            :data-skillValue="prop"
          >
            <span class="skill" :class="key">{{key}}:</span>
            <span class="skill" :class="key">{{" " + prop}}%</span>
          </li>
        </ul>
      </article>
      <article>
        <h1>Portfolio</h1>
        <section>
          <ul class="portfolio-box">
            <li v-for="(key) in repos" :key="key.url" class="portfolio-item">
              <h4>{{key.name}}</h4>
              <q>{{key.description }}</q>
              <br />
              <a :href="key.url">{{ key.url }}</a>
            </li>
          </ul>
        </section>
      </article>
    </div>
  </Standard>
</template>

<script>
// @ is an alias to /src
import Standard from "@/containers/Standard.vue";
import { Octokit } from "@octokit/core";
const octokit = new Octokit();

export default {
  name: "Home",
  components: { Standard },
  data() {
    return {
      repos: this.getRepos(),
      intro: {
        Name: "Kjetil",
        Nationality: "Norway",
        Born: "'89",
        Occupation: "Student working in retail",
        Availability: "Will consider all opportunities"
      },
      skills: {
        javascript: 80,
        typescript: 70,
        vuejs: 60,
        react: 50,
        css: 95,
        html: 85,
        python: 40
      },
      brands: {
        javascript: {
          gradient: "linear-gradient(120deg, #f7df1e, #FFFFFF)",
          color: "#f7df1e"
        },
        typescript: {
          gradient: "linear-gradient(120deg, #152740, #FFFFFF)",
          color: "rgb(41, 78, 128)"
        },
        vuejs: {
          gradient: "linear-gradient(120deg, #42b883, #35495e)",
          color: "#42b883"
        },
        react: {
          gradient: "linear-gradient(120deg, #00d8ff, #FFFFFF)",
          color: "#00d8ff"
        },
        css: {
          gradient: "linear-gradient(120deg, #123499, #FFFFFF)",
          color: "#123499"
        },
        html: {
          gradient: "linear-gradient(120deg, #e34f26, #FFFFFF)",
          color: "#e34f26"
        },
        python: {
          gradient: "linear-gradient(-120deg, #ffde57, #4584b6, #646464)",
          color: "#ffde57"
        }
      },
      colorGrades: [
        "red",
        "orangered",
        "tomato",
        "orange",
        "yellow",
        "greenyellow",
        "lawngreen",
        "lightgreen",
        "green",
        "gold"
      ]
    };
  },
  methods: {
    async getRepos() {
      await octokit
        .request("GET /users/{username}/repos", {
          username: "kjetilcodes"
        })
        .then(result => {
          console.log(result);
          this.repos = result.data.map(e => {
            return {
              url: e.html_url,
              name: e.name,
              description: e.description
            };
          });
        });
    },
    setBrandColor(key) {
      return `background: ${this.brands[key].gradient};`;
    }
  },
  mounted() {
    const skills = document.querySelectorAll(".skill-li-item");
    skills.forEach(skillItem => {
      const skillValue = skillItem.getAttribute("data-skillValue");
      const line = document.createElement("div");
      const brandName = skillItem
        .getAttribute("class")
        .replace("skill-li-item ", "");
      const { color } = this.brands[brandName];
      line.style.backgroundColor = color;
      line.style.minWidth = `${skillValue}%`;
      line.style.maxWidth = `${skillValue}%`;
      line.style.minHeight = "10px";
      line.style.maxHeight = "10px";
      line.style.borderRadius = "10px";
      line.style.padding = "5px";
      skillItem.insertBefore(line, skillItem.firstElementChild);
    });
  }
};
</script>

<style lang="scss">
.portfolio-item {
  border: 1px solid #00000044;
  border-radius: 10px;
  padding: 20px;
}
.skill-li-item {
  padding: 10px 23px;
  width: auto;
  border-radius: 10px;
}

.about-key {
  font-weight: bold;
}

.intro-li-item {
  display: flex;
  flex-direction: row;
  max-width: 400px;
  justify-content: space-between;
  span {
    margin: 4px 0;
  }
  .about-prop {
    width: 50%;
  }
}

@media (min-width: 700px) {
  .skill-box,
  .portfolio-box {
    display: grid;
    width: 100%;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: 1fr 1fr;
    gap: 20px;
    li {
      width: 80%;
    }
  }

  .skill-container,
  .portfolio-container {
    width: 100%;
  }
}
</style>
