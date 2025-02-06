<template>
  <div class="mx-auto max-w-2xl px-4 py-24 sm:px-6 sm:py-24 lg:px-8 bg-white-500 text-xs">
    <div class="mt-10 grid grid-cols-1 gap-x-1 gap-y-8 sm:grid-cols-[repeat(23,_minmax(0,_1fr))]">
      <div class="sm:col-span-1 bg-white rounded h-4 self-center">0hour</div>
      <div class="sm:col-start-3 sm:col-end-[23] bg-black rounded h-px self-center"></div>
      <div class="sm:col-span-1 bg-white rounded h-4 self-center">1hour</div>
    </div>
    <div class="mt-10 grid grid-cols-1 gap-x-1 gap-y-8 sm:grid-cols-[repeat(23,_minmax(0,_1fr))]">
      <div class="sm:col-span-3 bg-white rounded h-3 self-center">Thread 1:</div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
      <div
        class="sm:col-span-12 bg-gradient-to-r from-green-500 from-2% via-yellow-500 via-10% to-red-500 rounded h-3 self-center"
      ></div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
    </div>

    <div class="mt-10 grid grid-cols-1 gap-x-1 gap-y-8 sm:grid-cols-[repeat(23,_minmax(0,_1fr))]">
      <div class="sm:col-span-3 bg-white rounded h-3 self-center">Thread 2:</div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
      <div
        class="sm:col-span-12 bg-gradient-to-r from-green-500 from-2% via-yellow-500 via-10% to-red-500 rounded h-3 self-center"
      ></div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
    </div>
    <div class="mt-10 grid grid-cols-1 gap-x-1 gap-y-8 sm:grid-cols-[repeat(23,_minmax(0,_1fr))]">
      <div class="sm:col-span-3 bg-white rounded h-3 self-center">Thread 3:</div>
      <div
        class="sm:col-span-12 bg-gradient-to-r from-green-500 from-2% via-yellow-500 via-10% to-red-500 rounded h-3 self-center"
      ></div>
      <div
        class="sm:col-span-8 bg-gradient-to-r from-green-500 from-2% via-yellow-500 via-10% to-red-500 rounded h-3 self-center"
      ></div>
    </div>
    <div class="mt-10 grid grid-cols-1 gap-x-1 gap-y-8 sm:grid-cols-[repeat(23,_minmax(0,_1fr))]">
      <div class="sm:col-span-3 bg-white rounded h-3 self-center">Thread 4:</div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
      <div
        class="sm:col-[span_14_/_span_14] bg-gradient-to-r from-green-500 from-2% via-yellow-500 via-10% to-red-500 rounded h-3 self-center"
      ></div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
    </div>
    <div class="mt-10 grid grid-cols-1 gap-x-1 gap-y-8 sm:grid-cols-[repeat(23,_minmax(0,_1fr))]">
      <div class="sm:col-span-3 bg-white rounded h-3 self-center">Thread 5:</div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
      <div
        class="sm:col-span-12 bg-gradient-to-r from-green-500 from-2% via-yellow-500 via-10% to-red-500 rounded h-3 self-center"
      ></div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
    </div>
    <div class="mt-10 grid grid-cols-1 gap-x-1 gap-y-8 sm:grid-cols-[repeat(23,_minmax(0,_1fr))]">
      <div class="sm:col-span-3 bg-white rounded h-3 self-center">Thread 6:</div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
      <div
        class="sm:col-span-12 bg-gradient-to-r from-green-500 from-2% via-yellow-500 via-10% to-red-500 rounded h-3 self-center"
      ></div>
    </div>
    <div class="mt-10 grid grid-cols-1 gap-x-1 gap-y-8 sm:grid-cols-[repeat(23,_minmax(0,_1fr))]">
      <div class="sm:col-span-3 bg-white rounded h-3 self-center">Thread 7:</div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
      <div
        class="sm:col-[span_16_/_span_16] bg-gradient-to-r from-green-500 from-2% via-yellow-500 via-10% to-red-500 rounded h-3 self-center"
      ></div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
    </div>
    <div class="mt-10 grid grid-cols-1 gap-x-1 gap-y-8 sm:grid-cols-[repeat(23,_minmax(0,_1fr))]">
      <div class="sm:col-span-3 bg-white rounded h-3 self-center">Thread 8:</div>
      <div
        class="sm:col-[span_16_/_span_16] bg-gradient-to-r from-green-500 from-2% via-yellow-500 via-10% to-red-500 rounded h-3 self-center"
      ></div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
    </div>
    <div class="mt-10 grid grid-cols-1 gap-x-1 gap-y-8 sm:grid-cols-[repeat(23,_minmax(0,_1fr))]">
      <div class="sm:col-span-3 bg-white rounded h-3 self-center">Thread 9:</div>
      <div
        class="sm:col-[span_16_/_span_16] bg-gradient-to-r from-green-500 from-2% via-yellow-500 via-10% to-red-500 rounded h-3 self-center"
      ></div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
    </div>
    <div class="mt-10 grid grid-cols-1 gap-x-1 gap-y-8 sm:grid-cols-[repeat(23,_minmax(0,_1fr))]">
      <div class="sm:col-span-3 bg-white rounded h-3 self-center">Thread 10:</div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
      <div class="sm:col-span-2 bg-green-500 rounded h-3 self-center"></div>
      <div
        class="sm:col-[span_16_/_span_16] bg-gradient-to-r from-green-500 from-2% via-yellow-500 via-10% to-red-500 rounded h-3 self-center"
      ></div>
    </div>
  </div>
</template>
