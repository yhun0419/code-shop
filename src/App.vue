<script setup>
import { computed, ref } from 'vue'

const activeCuisine = ref('cantonese')
const isMenuOpen = ref(false)

const cuisines = [
  { id: 'cantonese', label: '粤菜' }, { id: 'hongkong', label: '港菜' },
  { id: 'sichuan', label: '川菜' }, { id: 'jiangnan', label: '江浙菜' },
  { id: 'japanese', label: '日式' }, { id: 'italian', label: '意式' }, { id: 'french', label: '法式' },
]

const menus = {
  cantonese: [
    { name: '金蒜蒸东星斑', desc: '陈年花雕 · 金蒜 · 葱油', price: '¥ 268', image: 'https://img.mingchu.co/ueditor/php/upload/image/20260128/69798c808398e.jpg' },
    { name: '黑叉烧拼盘', desc: '梅头肉 · 蜜汁 · 玫瑰露', price: '¥ 98', image: 'photo-1555939594-58d7cb561ad1' },
    { name: '鲜虾云吞面', desc: '大地鱼汤 · 竹升面 · 韭黄', price: '¥ 58', image: '/images/shrimp-wonton-noodles.jpg' },
  ],
  hongkong: [
    { name: '港式避风塘炒蟹', desc: '蒜酥 · 辣椒 · 葱花', price: '¥ 188', image: 'photo-1565299624946-b28f40a0ae38' },
    { name: '菠萝咕咾肉', desc: '黑毛猪 · 鲜菠萝 · 糖醋汁', price: '¥ 78', image: 'photo-1603133872878-684f208fb84b' },
    { name: '奶油猪仔包', desc: '港式炼乳 · 黄油 · 脆皮', price: '¥ 38', image: 'photo-1550507992-eb63ffee0847' },
  ],
  sichuan: [
    { name: '藤椒水煮牛肉', desc: '青花椒 · 菜籽油 · 黄牛肉', price: '¥ 128', image: 'photo-1547592180-85f173990554' },
    { name: '麻婆豆腐', desc: '汉源花椒 · 牛肉末 · 郫县豆瓣', price: '¥ 48', image: 'photo-1547592166-23ac45744acd' },
    { name: '川北凉粉', desc: '红油 · 花生 · 香醋', price: '¥ 32', image: 'photo-1505253716362-afaea1d3d1af' },
  ],
  jiangnan: [
    { name: '清蒸六月黄', desc: '姜醋 · 紫苏 · 绍兴黄酒', price: '¥ 148', image: 'photo-1559339352-11d035aa65de' },
    { name: '龙井虾仁', desc: '明前龙井 · 河虾 · 蛋清', price: '¥ 108', image: 'photo-1569058242253-92a9c755a0ec' },
    { name: '腌笃鲜', desc: '春笋 · 咸肉 · 土鸡清汤', price: '¥ 88', image: 'photo-1547592180-85f173990554' },
  ],
  japanese: [
    { name: '炙烧三文鱼握寿司', desc: '挪威三文鱼 · 柚子酱油 · 海苔', price: '¥ 88', image: 'photo-1579871494447-9811cf80d66c' },
    { name: '和牛寿喜烧', desc: 'M8 和牛 · 无菌蛋 · 关东葱', price: '¥ 198', image: 'photo-1515003197210-e0cd71810b5f' },
    { name: '豚骨叉烧拉面', desc: '慢熬骨汤 · 溏心蛋 · 笋干', price: '¥ 68', image: 'photo-1569718212165-3a8278d5f624' },
  ],
  italian: [
    { name: '松露野菌烩饭', desc: '意大利米 · 帕玛森 · 黑松露', price: '¥ 128', image: 'photo-1476124369491-e7addf5db371' },
    { name: '慢烤番茄布拉塔', desc: '布拉塔芝士 · 罗勒 · 酸面包', price: '¥ 78', image: 'photo-1572449043416-55f4685c9bb7' },
    { name: '黑松露意面', desc: '手工宽面 · 奶油 · 佩科里诺', price: '¥ 118', image: 'photo-1473093295043-cdd812d0e601' },
  ],
  french: [
    { name: '香煎鸭胸', desc: '樱桃汁 · 油封土豆 · 红酒', price: '¥ 168', image: 'photo-1544025162-d76694265947' },
    { name: '勃艮第红酒炖牛肉', desc: '牛颊肉 · 培根 · 珍珠洋葱', price: '¥ 148', image: 'photo-1534939561126-855b8675edd7' },
    { name: '焦糖布蕾', desc: '香草籽 · 焦糖脆壳 · 时令浆果', price: '¥ 66', image: 'photo-1470124182917-cc6e71b22ecc' },
  ],
}

const currentMenu = computed(() => menus[activeCuisine.value])
const imageUrl = (image) => image.startsWith('http') ? image : `https://images.unsplash.com/${image}?auto=format&fit=crop&w=800&q=85`
const selectCuisine = (id) => { activeCuisine.value = id }
const closeMenu = () => { isMenuOpen.value = false }
</script>

<template>
  <header class="site-header">
    <div class="container nav">
      <a class="brand" href="#top" @click="closeMenu"><span class="brand-mark">山</span>山海食集</a>
      <nav :class="{ open: isMenuOpen }">
        <a href="#story" @click="closeMenu">关于我们</a><a href="#special" @click="closeMenu">主厨推荐</a>
        <a href="#menu" @click="closeMenu">各地菜系</a><a href="#visit" @click="closeMenu">到店信息</a>
      </nav>
      <a class="nav-action" href="#visit">预订座位</a>
      <button class="menu-toggle" :aria-expanded="isMenuOpen" aria-label="打开菜单" @click="isMenuOpen = !isMenuOpen">☰</button>
    </div>
  </header>
  <main id="top">
    <section class="hero"><div class="hero-content"><div class="eyebrow">SEASONAL CHINESE KITCHEN</div><h1>把山海，端上餐桌</h1><p>从山野清晨到海岸黄昏，我们以当季食材，做一席有温度的中国菜。</p><a class="button" href="#menu">探索今日菜单 <span>→</span></a></div><div class="hero-info"><div><strong>营业时间</strong>11:30–14:00 · 17:30–22:00</div><div><strong>上海 · 徐汇</strong>衡山路 188 号</div></div></section>
    <section id="story" class="container intro"><div><div class="eyebrow sage">OUR PHILOSOPHY</div><h2>一口风味，<br>一段土地的记忆。</h2></div><div class="intro-copy"><p>我们相信，好食物并不需要复杂的修辞。它来自被认真对待的土壤、时令和人。主厨每周走访本地农场与渔港，只为找到最有生命力的那一味。</p><p>让每一次相聚，都从一顿好饭开始。</p><a class="text-link" href="#special">认识我们的厨房 →</a></div></section>
    <section id="special" class="feature"><div class="container feature-grid"><div class="feature-photo" role="img" aria-label="精致菜肴"></div><div class="feature-content"><span class="tag">CHEF'S SELECTION · 08</span><h2>慢炖 12 小时的<br>黑蒜牛肋</h2><p>选用谷饲牛小排，佐以发酵黑蒜、绍兴黄酒与时蔬清汤。时间让丰腴与醇厚在舌尖相遇。</p><div class="dish-note"><b>¥ 168</b><span>推荐搭配：福建岩茶 / 深色艾尔</span></div></div></div></section>
    <section id="menu" class="container menu"><div class="section-title"><div><div class="eyebrow sage">CULINARY REGIONS</div><h2>寻味各地菜系</h2></div><a class="text-link" href="#visit">查看完整菜单 →</a></div><div class="menu-tabs" role="tablist" aria-label="菜系分类"><button v-for="cuisine in cuisines" :key="cuisine.id" class="menu-tab" :class="{ active: activeCuisine === cuisine.id }" role="tab" :aria-selected="activeCuisine === cuisine.id" @click="selectCuisine(cuisine.id)">{{ cuisine.label }}</button></div><div class="menu-grid"><article v-for="dish in currentMenu" :key="dish.name" class="dish"><img :src="imageUrl(dish.image)" :alt="dish.name" /><div class="dish-bottom"><div><h3>{{ dish.name }}</h3><p>{{ dish.desc }}</p></div><span class="price">{{ dish.price }}</span></div></article></div></section>
    <section id="visit" class="booking"><div class="container booking-wrap"><div><div class="eyebrow">MAKE A RESERVATION</div><h2>等你赴约</h2></div><a class="button light" href="tel:021-55668899">立即预订 · 021 5566 8899</a></div></section>
  </main>
  <footer><div class="container footer"><span>© 2024 山海食集 SHANHAI KITCHEN</span><span>上海市徐汇区衡山路 188 号</span></div></footer>
</template>
