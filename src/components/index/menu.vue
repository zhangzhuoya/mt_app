<template>
  <div class="m-menu">
    <dl class="nav" @mouseleave="menuLeave">
      <dt>全部分类</dt>
      <dd v-for="(item, index) in menuList.data" :key="index" @mouseenter="menuEnter(item)">
        <i :class="item.type"></i>
        <span class="names">{{item.name}}</span>

        <span class="arrow"></span>
      </dd>
    </dl>
    <div v-if="curDetail" class="detail" @mouseenter="detailEnter" @mouseleave="detailLeave">
      <template v-for="(item, index) in curDetail.items">
        <h4 :key="index">{{item.title}}</h4>
        <span v-for="(v, i) in item.items" :key="v + '_'+ i">{{v}}</span>
      </template>
    </div>
  </div>
</template>
<script>
// import api from "@/api/index.js";
export default {
  data () {
    return {
      curDetail: null,
      menuList: {
        data: [
          {
            type: 'food',
            name: '美食',
            items: [
              {
                title: '美食',
                items: ['代金券', '甜点饮品', '火锅', '自助餐', '小吃快餐']
              }
            ]
          },
          {
            type: 'takeout',
            name: '外卖',
            items: [
              {
                title: '外卖',
                items: ['美团外卖']
              }
            ]
          },
          {
            type: 'hotel',
            name: '酒店',
            items: [
              {
                title: '星级酒店',
                items: ['经济型舒适/', '三星高档/', '四星豪华/']
              }
            ]
          },
          {
            type: 'homestay',
            name: '民宿',
            items: [
              {
                title: '热门城市',
                items: [
                  '上海',
                  '成都',
                  '北京',
                  '重庆',
                  '南京',
                  '杭州',
                  '广州',
                  '西安',
                  '武汉',
                  '厦门长沙',
                  '青岛',
                  '深圳',
                  '苏州'
                ]
              }
            ]
          },
          {
            type: 'movie',
            name: '电影',
            items: [
              {
                title: '热映电影',
                items: [
                  '多力特的奇幻冒险',
                  '误杀',
                  '喋血战士',
                  '抵达',
                  '之谜',
                  '刺猬',
                  '索尼克',
                  '寻梦环游记',
                  '疯狂动物',
                  '城白蛇',
                  '缘起',
                  '哪吒之魔童',
                  '降世',
                  '大鱼海棠'
                ]
              }
            ]
          },
          {
            type: 'airport',
            name: '飞机票/火车票',
            items: [
              {
                title: '机票',
                items: ['国内机票国际/', '港澳台机票']
              }
            ]
          },
          {
            type: 'ktv',
            name: '休闲娱乐 / KTV',
            items: [
              {
                title: '休闲娱乐',
                items: [
                  '足疗',
                  '按摩',
                  '洗浴',
                  '汗蒸',
                  '酒吧',
                  '密室',
                  '逃脱',
                  '轰趴馆',
                  '茶馆',
                  '私人影院',
                  'DIY手工',
                  '坊采摘',
                  '农家乐',
                  '网吧',
                  '网咖',
                  '游乐游艺',
                  'VR桌',
                  '面游戏',
                  '真人CS',
                  '棋牌室',
                  '其他',
                  '玩乐'
                ]
              }
            ]
          },
          {
            type: 'life',
            name: '生活服务',
            items: [
              {
                title: '生活服务',
                items: [
                  '衣物',
                  '皮具',
                  '洗护',
                  '家政',
                  '搬家',
                  '运输',
                  '送水',
                  '充值缴费',
                  '服饰/鞋',
                  '养护开锁',
                  '换锁',
                  '家维修',
                  '管道疏通',
                  '家电维修',
                  '清洗',
                  '电脑维修',
                  '手机维修',
                  '件照',
                  '肖像摄影',
                  '照片',
                  '印刷',
                  '图文文',
                  '印商务服',
                  '法律服务',
                  '文化传媒',
                  '机构',
                  '成人用品',
                  '情趣用品'
                ]
              }
            ]
          },
          {
            type: 'hair',
            name: '丽人 / 美发 / 医学美容',
            items: [
              {
                title: '丽人',
                items: [
                  '美发',
                  '美甲',
                  '美睫',
                  '美容',
                  '美体',
                  '医学美容',
                  '瑜伽',
                  '舞蹈',
                  '瘦身',
                  '纤体',
                  '韩式定妆',
                  '祛痘',
                  '纹身',
                  '化妆',
                  '养发'
                ]
              }
            ]
          },
          {
            type: 'marry',
            name: '结婚 / 婚纱摄影 / 婚宴',
            items: [
              {
                title: '外卖',
                items: [
                  '婚纱',
                  '摄影',
                  '旅拍',
                  '个性',
                  '写真婚',
                  '婚庆',
                  '公司',
                  '婚纱',
                  '礼服',
                  '西服',
                  '定制',
                  '婚戒',
                  '首饰',
                  '婚车',
                  '租赁',
                  '司仪',
                  '主持彩',
                  '型婚',
                  '跟拍',
                  '婚礼',
                  '小礼品',
                  '更多',
                  '婚礼服'
                ]
              }
            ]
          },
          {
            type: 'offspring',
            name: '亲子 / 儿童乐园 / 幼教',
            items: [
              {
                title: '外卖',
                items: [
                  '儿童乐园',

                  '婴儿游泳',
                  '亲子游乐',
                  '幼儿教育',
                  '早教中心',
                  '少儿英语',
                  '智力开发',
                  '托班',
                  '幼儿园',
                  '幼儿教育',
                  '儿童摄影',
                  '孕妇写真',
                  '上门拍',
                  '亲子摄影',
                  '孕产护理',
                  '月子会所',
                  '产后恢复',
                  '妇幼医院',
                  '孕产用品',
                  '开奶催乳',
                  '月嫂',
                  '亲子购物',
                  '宝宝派对',
                  '亲子服务'
                ]
              }
            ]
          },
          {
            type: 'sport',
            name: '运动健身 / 健身中心',
            items: [
              {
                title: '运动健身',
                items: [
                  '运动健身',
                  '健身中心',
                  '武术场馆',
                  '游泳馆羽',
                  '毛球馆',
                  '溜冰场',
                  '射箭馆',
                  '篮球场',
                  '网球馆',
                  '台球馆',
                  '乒乓球',
                  '足球场',
                  '高尔夫场',
                  '保龄球馆',
                  '体育场馆',
                  '马术场',
                  '壁球馆',
                  '更多运动'
                ]
              }
            ]
          },
          {
            type: 'furniture',
            name: '家装 / 建材 / 家居',
            items: [
              {
                title: '家居装修',
                items: ['装修设计',
                  '半包装修', '全包装修', '清包装修',
                  '装修建材',
                  '地板', '瓷砖', '石材', '橱柜', '灯饰照明', '厨卫洁具', '油漆涂料', '集成吊顶', '墙纸', '墙艺门', '窗木材板', '家用五金', '电工电料', '楼梯', '管材', '管件',
                  '家具家居',
                  '家具', '床上用品', '家纺家居', '饰品', '厨具', '餐具', '智能家居',
                  '家装卖场',
                  '建材卖场', '家居卖场']
              }
            ]
          },
          {
            type: 'study',
            name: '学习培训 / 音乐培训',
            items: [
              {
                title: '学习',
                items: ['音乐培训',
                  '钢琴', '吉他', '小提琴', '古筝', '架子鼓', '声乐', '音乐培训',
                  '职业技术',
                  '美容化妆', '会计', 'IT', '厨艺管理', '培训', '摄影培训', '司法考试', '公务员', '培训其他', '职业',
                  '外语培训',
                  '美术培训']
              }
            ]
          },
          {
            type: 'health',
            name: '医疗健康 / 宠物 / 爱车',
            items: [
              {
                title: '医疗',
                items: ['洗车', '租车', '加油站', '维修保养', '驾校汽车', '美容陪练', '汽车用品', '汽车保险4S店', '汽车', '销售', '配件']
              }
            ]
          },
          {
            type: 'takeout',
            name: '酒吧 / 密室逃脱',
            items: [
              {
                title: '玩乐',
                items: ['KTV酒吧', '密室逃脱', '游乐游艺', '网吧网咖', '私人影院', 'DIY手工坊', '桌面游戏', '采摘', '农家乐', '棋牌室', '轰趴馆', '真人CSVR']
              }
            ]
          }
        ]
      }
    }
  },
  created () {
    // api.getMenuList().then((res) => {
    //   this.menuList = res.data.data;
    //   console.log(this.menuList);
    // });
  },
  methods: {
    menuEnter (item) {
      console.log(item)
      this.curDetail = item
    },
    menuLeave () {
      var self = this
      this.timer = setTimeout(function () {
        self.curDetail = null
      }, 200)
    },
    detailEnter () {
      clearTimeout(this.timer)
    },
    detailLeave () {
      this.curDetail = null
    }
  }
}
</script>
