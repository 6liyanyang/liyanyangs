<template>
  <div id="box">
    <div id="box_top_son">
      <div class="head">
        <ul class="ul3">
          <li v-for="(tab, index) in tabs" :key="index" :class="{ actives: index === activeTab }"
            @click="activeTab = index">
            <div>
              {{ tab.text }}
            </div>
          </li>
        </ul>
      </div>
    </div>
    <!-- 这是身子 -->
    <div id="box_shenzi">
      <!-- 这是左边盒子 -->
      <div id="box_shenzi_zuo">
        <div class="leftdata">
          <ul>
            <li>
              <input type="text" v-model="searchTerm" placeholder="搜索 " @keyup.enter="funs">
            </li>
            <li>
              <draggable>
                <transition-group>
                  <el-tag v-for="(item, index) in str" :key="index" @click="activeTab = index"
                    :class="{ 'active': index === activeTab }">
                    <a href="#">
                      <svg data-v-d7b5176e xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"
                        viewBox="0 0 24 24" id="listers">
                        <path
                          d="M11 18c0 1.1-.9 2-2 2s-2-.9-2-2s.9-2 2-2s2 .9 2 2zm-2-8c-1.1 0-2 .9-2 2s.9 2 2 2s2-.9 2-2s-.9-2-2-2zm0-6c-1.1 0-2 .9-2 2s.9 2 2 2s2-.9 2-2s-.9-2-2-2zm6 4c1.1 0 2-.9 2-2s-.9-2-2-2s-2 .9-2 2s.9 2 2 2zm0 2c-1.1 0-2 .9-2 2s.9 2 2 2s2-.9 2-2s-.9-2-2-2zm0 6c-1.1 0-2 .9-2 2s.9 2 2 2s2-.9 2-2s-.9-2-2-2z"
                          fill="currentColor" />
                      </svg>
                      <img :src="item.imgse" alt width="20px" height="20px" />
                      <span>{{ item.name }}</span>
                      <b @click="deletFun(index)">...</b>
                    </a>
                  </el-tag>
                </transition-group>
              </draggable>
            </li>

          </ul>
        </div>
      </div>
      <div id="box_shenzi_you">
        <div class="rightdata">
          <ul class="ul4">

            <div id="list_box" v-if="activeTab == 0">
              <li class="li1">
                <img src="https://files.codelife.cc/topsearch/Jb0vmloB1G.png" alt width="25px" height="25px" />
                <span>百度.实时热点</span>
              </li>
              <li v-for="(item, index) in data" :key="index" class="list">
                <span :class="{
                  one: index == 0,
                  two: index == 1,
                  thre_son: index === 2
                }">{{ item.index }}</span>
                <span class="sp1">{{ item.title }}</span>
                <span class="sp2">{{ item.hotValue
                }}</span>
              </li>
            </div>

            <div id="list_box" v-if="activeTab == 1">
              <li class="li1">
                <img src="https://files.codelife.cc/topsearch/KqndgxeLl9.png" alt width="25px" height="25px" />
                <span>微博.热搜榜</span>
              </li>
              <li v-for="(item, index) in sondata" :key="index" class="list">
                <span :class="{
                  one: index == 0,
                  two: index == 1,
                  thre_son: index === 2
                }">{{ item.index }}</span>
                <span class="sp1">{{ item.title }}</span>
                <span class="sp2">{{ item.hotValue
                }}</span>
              </li>
            </div>

            <div id="list_box" v-if="activeTab == 2">
              <li class="li1">
                <img src="https://files.codelife.cc/topsearch/mproPpoq6O.png" alt width="25px" height="25px" />
                <span>知乎.热榜</span>
              </li>
              <li v-for="(item, index) in datason" :key="index" class="list">
                <span :class="{
                  one: index == 0,
                  two: index == 1,
                  thre_son: index === 2
                }">{{ item.index }}</span>
                <span class="sp1">{{ item.title }}</span>
                <span class="sp2">{{ item.hotValue
                }}</span>
              </li>
            </div>
            <div id="list_box" v-if="activeTab == 3">
              <li class="li1">
                <img src="https://files.codelife.cc/topsearch/Q1Vd5Ko85R.png" alt width="25px" height="25px" />
                <span>36氪 ‧ 24小时热榜</span>
              </li>
              <li v-for="(item, index) in datafoue" :key="index" class="list">
                <span :class="{
                  one: index == 0,
                  two: index == 1,
                  thre_son: index === 2
                }">{{ item.index }}</span>
                <span class="sp1">{{ item.title }}</span>
                <span class="sp2">{{ item.hotValue
                }}</span>
              </li>
            </div>
            <div id="list_box" v-if="activeTab == 4">
              <li class="li1">
                <img src="https://files.codelife.cc/topsearch/74KvxwokxM.png" alt width="25px" height="25px" />
                <span>哔哩哔哩 ‧ 全站日榜</span>
              </li>
              <li v-for="(item, index) in datafive" :key="index" class="list">
                <span :class="{
                  one: index == 0,
                  two: index == 1,
                  thre_son: index === 2
                }">{{ item.index }}</span>
                <span class="sp1">{{ item.title }}</span>
                <span class="sp2">{{ item.hotValue
                }}</span>
              </li>
            </div>
            <div id="list_box" v-if="activeTab == 5">
              <li class="li1">
                <img src="https://files.codelife.cc/topsearch/NKGoRAzel6.png" alt width="25px" height="25px" />
                <span>吾爱破解 ‧ 今日热帖</span>
              </li>
              <li v-for="(item, index) in datasix" :key="index" class="list">
                <span :class="{
                  one: index == 0,
                  two: index == 1,
                  thre_son: index === 2
                }">{{ item.index }}</span>
                <span class="sp1">{{ item.title }}</span>
                <span class="sp2">{{ item.hotValue
                }}</span>
              </li>
            </div>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import draggable from "vuedraggable";
import { data } from "../components/rightdata.js";
import { sondata } from "../components/rightdatare.js";
import { datason } from "../components/rightdatayi.js";
import { datafoue } from "../components/rightfoue";
import { datafive } from "../components/datafive";
import { datasix } from "../components/datasix";
export default {
  data() {
    return {
      searchTerm: '',
      data: data,
      sondata: sondata,
      datason: datason,
      datafoue: datafoue,
      datafive: datafive,
      datasix: datasix,
      str: [
        {
          imgse: "https://files.codelife.cc/topsearch/Jb0vmloB1G.png",
          name: "百度",
        },
        {
          imgse: "https://files.codelife.cc/topsearch/KqndgxeLl9.png",
          name: "微博"
        },
        {
          imgse: "https://files.codelife.cc/topsearch/mproPpoq6O.png",
          name: "知乎"
        },
        {
          imgse: "https://files.codelife.cc/topsearch/Q1Vd5Ko85R.png",
          name: "36氪"
        },
        {
          imgse: "https://files.codelife.cc/topsearch/74KvxwokxM.png",
          name: "哔哩哔哩"
        },
        {
          imgse: "https://files.codelife.cc/topsearch/NKGoRAzel6.png",
          name: "吾爱破解"
        },
      ],
      tabs: [
        {
          text: "我的订阅",
        },
        {
          text: "全部",
        },
        {
          text: "综合",
        },
        {
          text: "科技",
        },
        {
          text: "娱乐",
        },
        {
          text: "社区",
        },
      ],
      activeTab: 0,
    };
  },

  mounted() {
    console.log(this.data[0].index);
  },
  components: {
    draggable
  },

  methods: {
    deletFun(index) {
      console.log(index);
      if (confirm("确认删除吗")) {
        this.str.splice(index, 1)
      } else {
        return
      }

    },

    onEnd() {
      const tags = [].concat(this.tags);
      // 重置sort值
      tags.map((item, index) => {
        item.sort = index;
      });
      this.tags = tags;
    },
    funs() {
      return this.str.filter(item => item.name.includes(this.searchTerm));
    }
  }
}
</script>

<style lang="less" scoped>
#box_shenzi {

  //这是左边鹤子
  #box_shenzi_zuo {

    .leftdata {
      float: left;
      margin-top: 10px;
      width: 24%;
      height: 536px;
      border-top: 1px solid gray;
      border-right: 1px solid gray;
    }

    ul {
      width: 100%;
      height: 100%;
    }

    li {
      width: 100%;
      height: 30px;
      line-height: 25px;
    }

    li input {
      position: relative;
      left: 5px;
      width: 90%;
      height: 25px;
      border: none;

      border-radius: 10px;
      padding-left: 10px;
      background-color: #2a2a2c;
    }

    li a {
      position: relative;
      left: 10px;
      display: block;
      width: 80%;
      height: 30px;
    }

    li img {
      position: relative;
      top: 5px;
      border-radius: 5px;
    }

    li span {
      position: relative;
      left: 5px;
      font-size: 15px !important;
      color: #fff;
    }

    li b {
      position: relative;
      top: -3px;
      left: 8px;
      float: right;
      color: #fff;
    }

    #listers {
      position: relative;
      top: 5px;
      width: 20px;
      height: 20px;
      color: #fff;
    }

    li span:hover {
      color: blue;
    }

    li b:hover {
      color: blue;
    }
  }

  #box_shenzi_you {

    .one {
      background-color: #fe2d46 !important;
    }

    .two {
      background-color: #f60 !important;
    }

    .thre_son {
      background-color: #faa90e !important;

    }

    #list_box {
      li {
        span:nth-child(1) {
          display: inline-block;
          width: 20px;
          height: 20px;
          background-color: gray;
          text-align: center;
          color: #fff;
          border-radius: 2px;
          line-height: 20px;
        }
      }
    }

    .rightdata {
      margin-top: -13.8px;
      float: right;
      width: 75.87%;
      height: 512px;
      border-top: 1px solid gray;
    }

    ul {
      width: 90%;
      height: 100%;
      margin: auto;
    }

    .li1 {
      width: 100%;
      height: 40px;
      border-bottom: 1px solid gray;
    }

    .li1 img {
      position: relative;
      top: 7px;
      border-radius: 50%;
    }

    .li1 span {
      position: relative;
      left: 5px;
      color: #fff;
    }

    .sp1 {
      margin-left: 2%;
      color: #fff;
    }

    .sp2 {
      float: right;
      color: #fff;
    }

    .list {
      margin-top: 10px;
    }

  }
}


ul li {
  list-style: none;
}

.head {
  width: 95%;
  height: 40px;
  margin: auto;
  border-bottom: 3px solid gray;
}

.ul3 {
  width: 100%;
  height: 40px;
  line-height: 40px;
  display: flex;
  justify-content: space-around;
}

.ul4 {
  width: 100%;
  height: 40px;
  line-height: 40px;
}

li {
  font-size: 14px;
  color: #dfeaf3;
}

.list {
  width: 800px;
}

#list_box {
  width: 100%;
  height: 500px;
}

.li1 {
  width: 800px;
}

#box_shenzi #box_shenzi_you .rightdata[data-v-b8406f7e] {
  margin-top: 10.2px;
  float: right;
  width: 75.87%;
  height: 498px;
  border-top: 1px solid gray;
}

el-tag {
  display: block;
  width: 85%;
  height: 100%;
}

.active {
  background-color: #1089ff;
}

.actives {
  color: #1089ff;
  border-bottom: 3px solid #1089ff;
}
</style>
