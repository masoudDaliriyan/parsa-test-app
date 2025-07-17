<template>
  <header class="bg-[#242629] w-full py-2">
    <div class="max-w-[1200px] w-full mx-auto">
      <div class="w-full flex items-center justify-between py-2  sm:px-0">
        <div class="flex items-center space-x-4">
          <img src="/film-tarsnak-logo.svg" alt="logo" >
          <div class="hidden md:block">
            <nav class="flex space-x-2 sm:space-x-4">
              <a href="#section1" class="px-2 py-1 bg-[##1B1C1F] sm:px-3 rounded text-gray-700 text-sm sm:text-base">دسته بندی ها</a>
              <a href="#section2" class="px-2 py-1 bg-[##1B1C1F] sm:px-3 rounded text-gray-700 text-sm sm:text-base">فیلم</a>
              <a href="#section2" class="px-2 py-1 bg-[##1B1C1F] sm:px-3 rounded text-gray-700 text-sm sm:text-base">سریال</a>
              <a href="#section3" class="px-2 py-1 bg-[##1B1C1F] sm:px-3 rounded text-gray-700 text-sm sm:text-base">بازیگران</a>
            </nav>
          </div>
        </div>
        <div class="flex space-x-2 sm:space-x-4">
          <div class="w-10 h-10 sm:w-12 sm:h-12 flex justify-center items-center bg-[#1B1C1F] rounded-lg  p-2 sm:px-4 sm:py-2 hover:bg-blue-600">
            <img src="/icons/notification.svg" alt="search" class="w-4 h-4">
          </div>
          <div class="w-10 h-10 sm:w-12 sm:h-12 flex justify-center items-center bg-[#1B1C1F] rounded-lg  p-2 sm:px-4 sm:py-2 hover:bg-blue-600">
            <img src="/icons/tag.svg" alt="search" class="w-4 h-4">
          </div>
          <div class="w-10 h-10 sm:w-12 sm:h-12 flex justify-center items-center bg-[#1B1C1F] rounded-lg  p-2 sm:px-4 sm:py-2 hover:bg-blue-600">
            <img src="/icons/search.svg" alt="search" class="w-4 h-4">
          </div>
          <div class="w-10 h-10 sm:w-12 sm:h-12 flex justify-center items-center bg-[#1B1C1F] rounded-lg  p-2 sm:px-4 sm:py-2 hover:bg-blue-600">
            <img src="/icons/profile.svg" alt="search" class="w-4 h-4">
          </div>
        </div>
      </div>
    </div>
  </header>
  
  <div class="max-w-[1200px] w-full mx-auto px-4 sm:px-0 !mb-8">
    <div class="py-4 my-[15px] ">
      <div class=" flex gap-2 items-center justify-end">
        <div class="flex gap-2 bg-[#242629] p-4 rounded-sm">
          <img src="/icons/back-gray.svg" alt="">
          <span class="text-sm sm:text-base">
            بازگشت
          </span>
        </div>
      </div>
    </div>
    
    <div class="space-y-4">
      <div class="flex flex-col sm:flex-row justify-between gap-4">
        <div class="flex text-right items-center">
          <div class="flex flex-col sm:flex-row gap-2 sm:gap-4">
            <img src="/icons/1080.svg" alt="1080" class="ml-0 sm:ml-4 w-10 h-10">
            <div>
              <div class="text-lg sm:text-2xl">
                {{ seriesData?.title_fa }}
              </div>
              <div class="text-sm sm:text-base">
                {{ seriesData?.title_en }}
              </div>
            </div>
          </div>
        </div>
        <div class="flex flex-wrap gap-2 sm:gap-4 items-center justify-end">
          <div class="flex gap-2 items-center text-sm sm:text-base">
            <span>
              <img src="/icons/play-circle.svg" class="w-4 h-4">
            </span>
            <span>
              فصل ۲ قسمت ۵
            </span>
          </div>
          <div class="flex items-center">
            <Rating v-if="seriesData" v-model="seriesData.user_rating" :max-rating="5" :readonly="true" class="mr-2" />
          </div>
          <div class="flex gap-2 items-center text-sm sm:text-base">
            <span>
              10 / {{ seriesData?.imdb }} 
            </span>
            <img src="/icons/imdb.svg" alt="imdb" class="w-6 h-6">
          </div>
          <div class="flex gap-2">
            <div class="w-10 h-10 sm:w-12 sm:h-12 flex justify-center items-center bg-[#242629] rounded-lg  p-2 sm:px-4 sm:py-2 hover:bg-blue-600">
              <img src="/icons/bookmarking.svg" alt="booking" class="w-4 h-4">
            </div>
            <div class="w-10 h-10 sm:w-12 sm:h-12 flex justify-center items-center bg-[#242629] rounded-lg  p-2 sm:px-4 sm:py-2 hover:bg-blue-600">
              <img src="/icons/share.svg" alt="booking" class="w-4 h-4">
            </div>
          </div>
        </div>
      </div>
      
      <div class="flex flex-col lg:flex-row gap-4 mt-4">
        <div class="w-full lg:w-2/3">
          <div class="w-full" style="margin-bottom: 16px;">
            <video
              ref="videoPlayer"
              class="video-js w-full h-auto aspect-[16/9] vjs-default-skin"
              controls
              preload="auto"
              poster="https://filmtarsnak.com/wp-content/uploads/2024/12/Sijjin-7-68165.jpg"
            >
              <track
                kind="subtitles"
                src="https://s600.upera.tv/s3/files/subtitles/ff5bf080-b157-11ef-918d-7b1c7b6ce523/subtitle_6750894197675.vtt"
                srclang="fa"
                label="فارسی"
                default
              />
            </video>
          </div>
          
          <div class="flex flex-col sm:flex-row justify-between !text-[12px] gap-2">
            <div class="flex flex-wrap gap-2">
              <div class="inline-block bg-[#AB070F99] px-4 py-2 rounded  sm:px-5 sm:py-2.5">
                پلیر تلوزیون های سامسونگ
              </div>
              <div class="inline-block bg-[#242629] px-4 py-2 rounded  sm:px-5 sm:py-2.5">
                پلیر تلوزیون های قدیمی
              </div>
              <div class="inline-block bg-[#242629] px-4 py-2 rounded  sm:px-5 sm:py-2.5">
                پلیر تلوزیون های قدیمی
              </div>
            </div>
            <div class="flex items-center gap-2 ">
              حین تماشا با مشکلی رو به رو شدید؟
              <div class="inline-block bg-[#242629] px-4 py-2 rounded  sm:px-5 sm:py-2.5">
                اعلام مشکل
              </div>
            </div>
          </div>
          
          <div class="flex flex-col sm:flex-row justify-between p-4 rounded-xl mt-4 gap-2 bg-[#2E2217]">
            <div class="flex items-center">
              <img src="/icons/danger.svg" class="ml-2 " alt="">
              <span class="text-sm sm:text-base">
                پیش از شروع تماشای آنلاین وی پی ان خود را خاموش کنید
              </span>
            </div>
            <div class="p-2 self-end sm:self-center border border-[#FB7800] !bg-[#1B1C1F] !text-[#FB7800] rounded-md">
              خرید اشتراک
            </div>
          </div>
          <div class="mt-4 p-4 rounded-xl bg-[#242629]">
            <div class="text-lg sm:text-xl">
              آیا تماشای سریال الکامینو را به دیگران پیشنهاد می کنید؟
            </div>
            <div class="text-sm sm:text-base mt-4">
              نظر خود را در این رابطه بنویسید
            </div>
            <textarea class="w-full mt-4 h-[150px] sm:h-[250px] p-4 bg-[#1B1C1F] border-none resize-none rounded-[5px] text-white" placeholder="متن نظر"></textarea>
            <div class="flex flex-col sm:flex-row  items-start sm:items-center mt-4 gap-4">
              <Rating v-model="ratingValue" :max-rating="5" class="mr-2" :isDisabled="hasRated"/>
              <button
                class="p-2 bg-[#AB070F] rounded-xl text-sm sm:text-base cursor-pointer"
                :class="{ 'opacity-50': hasRated }"
                @click="submitRating"
                :disabled="hasRated"
              >
                ارسال نظر
              </button>
            </div>
          </div>
        </div>
        <div class="w-full lg:w-1/3">
          <div class="flex flex-wrap gap-4">
            <div v-for="ep in seriesData?.episodes || []" :key="ep.number" class="flex gap-2 w-full">
              <img class="rounded-[6px] object-cover w-20 h-28 sm:w-24 sm:h-32" :src="ep.poster || '/sample-image.svg'" alt="">
              <div class="flex flex-col justify-between flex-1">
                <div>
                  <div class="text-base sm:text-lg">
                    {{ seriesData?.title_fa || 'فیلم EL CAMINO' }}
                  </div>
                  <div class="text-xs sm:text-sm">
                    فصل ۱ قسمت {{ ep.number || '۱' }}
                  </div>
                </div>
                <div class="flex gap-2 mt-2">
                  <div class="!flex !p-2 text-sm bg-[#43B100] text-white rounded w-fit">
                    <img src="/icons/fire.svg" class="w-4 h-4">
                  </div>
                  <div class="!flex !p-2 items-center bg-[#245DEF] text-white rounded gap-1 text-xs sm:text-sm w-fit">
                    <img src="/icons/microphone.svg" alt="" class="w-4 h-4">
                    <span class="ml-1">زیرنویس</span>
                  </div>
                  <div class="!flex !p-2 bg-[#FB7800] text-white rounded w-fit">
                    <img src="/icons/fire.svg" alt="" class="w-4 h-4">
                    دوبله
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount, watch } from 'vue'
import Rating from '~/components/Rating.vue'
import videojs from 'video.js'
import 'video.js/dist/video-js.css'

let seriesData = ref(null)
const videoPlayer = ref(null)
let player = null
const ratingValue = ref(4.5)
const hasRated = ref(false)

onMounted(async () => {
  player = videojs(videoPlayer.value, {
    controls: true,
    autoplay: false,
    preload: 'auto',
    fluid: true,
    sources: [
      {
        src: 'https://traffic.upera.tv/3025234-0-hls.m3u8?ref=uVhD',
        type: 'application/x-mpegURL',
      },
    ],
  })

  try {
    const res = await fetch('https://ylnk.site/test/?action=info&id=2501')
    if (res.ok) {
      seriesData.value = await res.json()
    }
  } catch (e) {
    console.error('Failed to fetch series data', e)
  }
  // Check if user has already rated
  hasRated.value = !!localStorage.getItem('hasRated_2501')
})

watch(seriesData, (val) => {
  if (val && val.imdb_rating) {
    ratingValue.value = val.imdb_rating
  }
})

const submitRating = async () => {
  try {
    const res = await fetch('https://ylnk.site/test/?action=rate&id=2501', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({ rate: ratingValue.value }),
    });

    const data = await res.json();
    ratingValue.value = 0
    seriesData.value = { ...seriesData.value, user_rating: data.new_rating }

    if (res.ok) {
      seriesData.user_rating = data.new_rating;
      alert('نظر شما با موفقیت ثبت شد!');
      hasRated.value = true
      localStorage.setItem('hasRated_2501', 'true')
    } else {
      alert('ثبت نظر با خطا مواجه شد.');
    }
  } catch (e) {
    console.error(e);
    alert('ثبت نظر با خطا مواجه شد.');
  }
};

onBeforeUnmount(() => {
  if (player) {
    player.dispose()
  }
})
</script>
