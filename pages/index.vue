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
    <div class="flex">
<div>
      <div class="flex">
        <div>
          <img src="/icons/1080.svg" alt="1080">
          سریال EL CAMINO
        </div>
        <div>
          فیلم ال کامینو
        </div>
        <div>
          <img src="/icons/play-circle.svg">
          فصل ۲ قسمت ۵
        </div>
        <div>
          <img src="/icons/imdb.svg" alt="imdb">
          <img src="/icons/bookmarking.svg" alt="booking">
        </div>
      </div>
      <div> 
        <img src="/video.svg">
      </div>
    </div>

    </div>
      </div>
</template>

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
.second-toolbar{
  margin: 15px 0 ;
  text-align: left;
}
</style> 