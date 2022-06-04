<template>
  <div class="light">
    <HeaderCont />
    <main id="main">
      <section id="referCont">
        <div className="container">
          <TitleCont name1="REFERENCE" name2="SITE" />
          <div class="refer__cont">
            <div class="table">
              <h3>HTML</h3>
              <ul>
                <li v-for="refer in refers" :key="refer.id">
                  <a href="/reference">
                    <span className="num">{{ refer.id }}</span>
                    <span className="attr">{{ refer.title }}</span>
                    <span className="desc">{{ refer.desc2 }}</span>
                    <span className="Inline">{{ refer.use }}</span>
                  </a>
                </li>
              </ul>
            </div>
          </div>
        </div>
        <ContactCont />
      </section>
    </main>
    <FooterCont />
  </div>
</template>

<script>
import HeaderCont from "@/components/HeaderCont.vue";
import FooterCont from "@/components/FooterCont.vue";
import TitleCont from "@/components/TitleCont.vue";
import ContactCont from "@/components/ContactCont.vue";

export default {
  components: {
    HeaderCont,
    FooterCont,
    TitleCont,
    ContactCont,
  },
  setup() {
    const refers = ref([]);

    const Reference = () => {
      fetch(
        "https://webstoryboy.github.io/react5001/src/assets/json/refer.json"
      )
        .then((response) => response.json())
        .then((data) => {
          refers.value = data.data.htmlRefer;
          // console.log(data.data.htmlRefer);
        });
    };

    Reference();

    return {
      refers,
      Reference,
    };
  },
};
</script>

<style lang="scss">
//refer__cont
#referCont {
  background: #f0eeeb;
  color: #fff;
  padding-bottom: 300px;
  color: #000;
}
.refer__cont {
  .table {
    border-bottom: 2px solid #fff;
    margin-top: 1.2rem;

    h3 {
      padding-bottom: 10px;
    }

    li {
      margin: 0;
      list-style: none;
      border-top: 1px solid #fff;
      position: relative;
      transition: all 0.3s;
      overflow: hidden;

      &:hover {
        background: rgba(255, 255, 255, 0.081);
      }

      span {
        display: inline-block;
        float: left;
        padding: 25px 10px;
        font-size: 14px;
        font-family: "S-CoreDream-3Light";
        box-sizing: border-box;

        &:nth-child(1) {
          width: 5%;
          text-align: center;
        }
        &:nth-child(2) {
          width: 10%;
        }
        &:nth-child(3) {
          width: 70%;
        }
        &:nth-child(4) {
          width: 15%;
          text-align: center;
        }
      }
    }
  }
}
</style>
