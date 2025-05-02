<script setup>
const props = defineProps({
  prefecture: String
})
const emit = defineEmits(['update:prefecture'])

const onChange = (event) => {
  emit('update:prefecture', event.target.value)
}
</script>

<template>
  <label for="prefecture">都道府県 : </label>
  <select id="prefecture" :value="props.prefecture" @change="onChange">
  <option value="" disabled>選択してください</option>
  <option value="Sapporo,jp">北海道</option>
  <option value="Aomori,jp">青森県</option>
  <option value="Morioka,jp">岩手県</option>
  <option value="Sendai,jp">宮城県</option>
  <option value="Akita,jp">秋田県</option>
  <option value="Yamagata,jp">山形県</option>
  <option value="Fukushima,jp">福島県</option>
  <option value="Mito,jp">茨城県</option>
  <option value="Utsunomiya,jp">栃木県</option>
  <option value="Maebashi,jp">群馬県</option>
  <option value="Saitama,jp">埼玉県</option>
  <option value="Chiba,jp">千葉県</option>
  <option value="Tokyo,jp">東京都</option>
  <option value="Yokohama,jp">神奈川県</option>
  <option value="Niigata,jp">新潟県</option>
  <option value="Toyama,jp">富山県</option>
  <option value="Kanazawa,jp">石川県</option>
  <option value="Fukui,jp">福井県</option>
  <option value="Kofu,jp">山梨県</option>
  <option value="Nagano,jp">長野県</option>
  <option value="Gifu,jp">岐阜県</option>
  <option value="Shizuoka,jp">静岡県</option>
  <option value="Nagoya,jp">愛知県</option>
  <option value="Tsu,jp">三重県</option>
  <option value="Otsu,jp">滋賀県</option>
  <option value="Kyoto,jp">京都府</option>
  <option value="Osaka,jp">大阪府</option>
  <option value="Kobe,jp">兵庫県</option>
  <option value="Nara,jp">奈良県</option>
  <option value="Wakayama,jp">和歌山県</option>
  <option value="Tottori,jp">鳥取県</option>
  <option value="Matsue,jp">島根県</option>
  <option value="Okayama,jp">岡山県</option>
  <option value="Hiroshima,jp">広島県</option>
  <option value="Yamaguchi,jp">山口県</option>
  <option value="Tokushima,jp">徳島県</option>
  <option value="Takamatsu,jp">香川県</option>
  <option value="Matsuyama,jp">愛媛県</option>
  <option value="Kochi,jp">高知県</option>
  <option value="Fukuoka,jp">福岡県</option>
  <option value="Saga,jp">佐賀県</option>
  <option value="Nagasaki,jp">長崎県</option>
  <option value="Kumamoto,jp">熊本県</option>
  <option value="Oita,jp">大分県</option>
  <option value="Miyazaki,jp">宮崎県</option>
  <option value="Kagoshima,jp">鹿児島県</option>
  <option value="Naha,jp">沖縄県</option>
</select>

</template>
