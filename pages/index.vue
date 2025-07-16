<template>
  <header class="header">
    <div class="container">
      <div class="w-full shadow flex items-center justify-between px-6 py-4">
        <div class="flex items-center space-x-4">
          <img src="/film-tarsnak-logo.svg" alt="logo" class="w-10 h-10 pl-8">
          <div class="header-links-wrapper">
            <nav class="flex">
              <a href="#section1" class="px-3 py-1 rounded hover:bg-gray-100 text-gray-700">دسته بندی ها</a>
              <a href="#section2" class="px-3 py-1 rounded hover:bg-gray-100 text-gray-700">فیلم</a>
              <a href="#section2" class="px-3 py-1 rounded hover:bg-gray-100 text-gray-700">سریال</a>
              <a href="#section3" class="px-3 py-1 rounded hover:bg-gray-100 text-gray-700">بازیگران</a>
            </nav>
          </div>
        </div>
        <div class="flex header__icons">
          <div class="bg-blue-500 px-4 py-2 rounded hover:bg-blue-600 icon-wrapper">
            <img src="/icons/notification.svg" alt="search" class="w-4 h-4">
          </div>
          <div class="bg-blue-500 px-4 py-2 rounded hover:bg-blue-600 icon-wrapper">
            <img src="/icons/tag.svg" alt="search" class="w-4 h-4">
          </div>
          <div class="bg-blue-500 px-4 py-2 rounded hover:bg-blue-600 icon-wrapper">
            <img src="/icons/search.svg" alt="search" class="w-4 h-4">
          </div>
          <div class="bg-blue-500 px-4 py-2 rounded hover:bg-blue-600 icon-wrapper">
            <img src="/icons/profile.svg" alt="search" class="w-4 h-4">
          </div>
        </div>
      </div>
    </div>
  </header>
  <div class="container">
    <div class="second-toolbar">
      <div class="button">
        <img src="/icons/back-gray.svg" alt="">
        بازگشت
      </div>
    </div>
    <div>
      <div class="flex justify-between">
        <div class="flex text-right items-center">
          <div class="flex">
            <img src="/icons/1080.svg" alt="1080">
            <div>
              <div>
                سریال EL CAMINO
              </div>
              <div>
                فیلم ال کامینو
              </div>
            </div>
          </div>
          <div>
          </div>
        </div>
        <div class="flex">
          <div>
            <img src="/icons/play-circle.svg">
            فصل ۲ قسمت ۵
          </div>
          <div>
            <img src="/icons/star.svg">
            <img src="/icons/star-gray.svg">
          </div>
          <div>
            <div>
              ۴.۵/۱۰
              <img src="/icons/imdb.svg" alt="imdb">
            </div>
          </div>
          <div class="flex">
            <div class="icon-wrapper button-icon">
              <img src="/icons/bookmarking.svg" alt="booking">
            </div>
            <div class="icon-wrapper button-icon">
              <img src="/icons/share.svg" alt="booking">
            </div>
          </div>
        </div>
      </div>
      <div class="flex">
        <div>
          <!-- Replace video image with Video.js player -->
          <div style="width: 790px; margin-bottom: 16px;">
            <video
              ref="videoPlayer"
              class="video-js vjs-default-skin"
              controls
              preload="auto"
              width="790"
              height="445"
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
          <div class="flex justify-between">
            <div>
              <div class="button">
                پلیر تلوزیون های سامسونگ
              </div>
              <div class="button">
                پلیر تلوزیون های قدیمی
              </div>
              <div class="button">
                پلیر تلوزیون های قدیمی
              </div>
            </div>
            <div>
              حین تماشا با مشکلی رو به رو شدید؟
              <div class="button">
                  اعلام مشکل
              </div>
            </div>

          </div>
                  </div>
        <div>
          <div class="flex flex-wrap gap-4">
            <div v-for="ep in seriesData?.episodes || []" :key="ep.number" class="flex">
              <img :src="ep.poster || '/sample-image.svg'" alt="">
              <div>
                <div>
                  <div>
                    {{ seriesData?.title_fa || 'فیلم EL CAMINO' }}
                  </div>
                  <div>
                    فصل ۱
                    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
                    قسمت {{ ep.number || '۱' }}
                  </div>
                </div>
                <div class="button button-orange">
                  <img src="/icons/fire.svg">
                </div>
                <div class="button button-blue">
                  <img src="/icons/microphone.svg" alt="">
                  زیرنویس
                </div>
                <div class="button button-green">
                  <img src="/icons/fire.svg" alt="">
                  دوبله
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
import { ref, onMounted, onBeforeUnmount } from 'vue'
import videojs from 'video.js'
import 'video.js/dist/video-js.css'

// Define seriesData so it is available in the template
const seriesData = ref(null)

const videoPlayer = ref(null)
let player = null

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

  // Fetch the series data
  try {
    const res = await fetch('https://ylnk.site/test/?action=info&id=2501')
    if (res.ok) {
      seriesData.value = await res.json()
    }
  } catch (e) {
    console.error('Failed to fetch series data', e)
  }
})

onBeforeUnmount(() => {
  if (player) {
    player.dispose()
  }
})
</script>

<style scoped>
.header {
  background-color: #242629;
  max-width: 1800px;
  padding: 10px 0 ;
}

.container {
  max-width: 1200px;
  width: 100%;
  margin: 0 auto;
}

.icon-wrapper {
  width: 48px;
  height: 48px;
  display: flex;  
  justify-content: center;
  align-items: center;
  background: #1B1C1F;
  border-radius: 8px;
}

.header__icons {
  gap: 5px;
}

.header-links-wrapper a {
  margin-right: 10px;
}

.button{
  display: inline-block;
  background-color: #242629;
  padding: 10px 20px;
  border-radius: 4px  ;
}
.button-green {
  background-color: #43B100;
  color: #fff;
}
.button-blue {
  background-color: #245DEF;
  color: #fff;
}
.button-orange {
  background-color: #FB7800;
  color: #fff;
}

.second-toolbar{
  margin: 15px 0 ;
  text-align: left;
}

.button-icon {
  background-color: #242629;
  border-radius: 4px;
  margin-left: 8px;
}
</style> 