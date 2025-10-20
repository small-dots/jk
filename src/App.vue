<script setup>
import { onMounted } from "vue";
import HelloWorld from "./components/HelloWorld.vue";
import autofit from "autofit.js";

onMounted(() => {
  // autofit.init();
  autofit.init({
    dh: 1025,
    dw: 1600,
    el: "body",
    resize: true,
  });
});
</script>

<template>
  <!-- 顶部导航栏 -->
  <div class="navbar" id="navbar">
    <div class="navbar-title"></div>
    <div class="title">xxx 可视化监控平台</div>
    <div class="datetime">2025-10-13 12:03:55 星期一</div>
  </div>
  <div class="absolute search top-[12%] z-[100] right-20 w-[200px]" id="search">
    <div
      class="absolute w-10 border border-gray-700 left-[-40px] top-0 h-full px-2 py-4 flex items-center justify-center bg-gray-700 rounded-l-lg pointer-events-none"
    >
      <span class="text-white font-semibold text-lg">CA</span>
    </div>
    <input
      type="text"
      placeholder="关键词搜索"
      class="w-full px-6 py-2 bg-gray-800 text-sm text-white placeholder-gray-400 rounded-r-lg border border-gray-700 focus:border-blue-500 focus:outline-none transition-colors duration-200"
    />
    <button
      class="absolute text-sm right-2 top-1/2 transform -translate-y-1/2 bg-blue-600 hover:bg-blue-700 text-white px-4 py-1 rounded-md transition-colors duration-200 font-medium"
    >
      搜索
    </button>
  </div>
  <aside
    class="absolute z-[100] bg-[#212f3c] right-0 top-[150px] right-0 w-[fit-content] rounded-l-xl shadow-md p-2 flex-row items-center"
    role="toolbar"
    aria-label="绘图工具栏"
  >
    <!-- 工具按钮组 -->
    <div
      id="toolList"
      class="flex-1 w-full space-y-2 flex flex-col items-center"
    >
      <button
        class="toolbar-button w-8 h-8 rounded-lg flex items-center justify-center"
        data-tool="point"
        title="点（Point）"
        aria-pressed="false"
      >
        <i class="fa fa-dot-circle-o fa-lg text-white" aria-hidden="true"></i>
      </button>

      <button
        class="toolbar-button w-8 h-8 rounded-lg flex items-center justify-center"
        data-tool="line"
        title="直线（Line）"
        aria-pressed="false"
      >
        <i class="fa-solid fa fa-minus fa-lg text-white" aria-hidden="true"></i>
      </button>

      <button
        class="toolbar-button w-8 h-8 rounded-lg flex items-center justify-center"
        data-tool="rect"
        title="矩形（Rectangle）"
        aria-pressed="false"
      >
        <i class="fa fa-square-o fa-lg text-white" aria-hidden="true"></i>
      </button>

      <button
        class="toolbar-button w-8 h-8 rounded-lg flex items-center justify-center"
        data-tool="circle"
        title="圆（Circle）"
        aria-pressed="false"
      >
        <i class="fa fa-circle-o fa-lg text-white" aria-hidden="true"></i>
      </button>

      <button
        class="toolbar-button w-8 h-8 rounded-lg flex items-center justify-center"
        data-tool="erase"
        title="擦除（Eraser）"
        aria-pressed="false"
      >
        <i class="fa fa-eraser fa-lg text-white" aria-hidden="true"></i>
      </button>

      <button
        class="toolbar-button w-8 h-8 rounded-lg flex items-center justify-center"
        data-tool="free"
        title="自由绘制（Free Draw）"
        aria-pressed="false"
      >
        <i class="fa fa-openid fa-lg text-white" aria-hidden="true"></i>
      </button>
    </div>
  </aside>
  <div
    id="gj"
    class="absolute transition-all duration-300 left-[400px] bottom-[-25%] z-[100] w-[50%] bg-gray-800 rounded-lg shadow-lg p-2"
  >
    <!-- 顶部标题栏 -->
    <div class="flex items-center justify-between mb-2 relative">
      <canvas id="altitudeChart"></canvas>
      <div class="flightReplayPlaybackButtonsContainer">
        <div class="flightReplayPlaybackModeIndicator">在途</div>
        <div
          role="button"
          aria-label="Play flight"
          tabindex="0"
          class="flightReplayButton play"
        >
          <div class="flightReplayButtonLabel">重放</div>
          <div class="flightReplayButtonIcon"></div>
        </div>
        <div
          role="button"
          aria-label="Change replay speed"
          tabindex="0"
          class="flightReplayButton playbackRate"
        >
          <div class="flightReplayButtonLabel">速度</div>
          <div class="flightReplayButtonIcon"></div>
          <div class="flightReplayButtonLabel">10x</div>
        </div>
        <div class="flightReplayButton loop" style="display: none">
          <div class="flightReplayButtonLabel">循环</div>
          <div class="flightReplayToggle">
            <div class="flightReplayTogglePaddle"></div>
          </div>
          <div class="flightReplayButtonLabel"></div>
        </div>
      </div>
      <div class="flightReplayScrubberContainer">
        <div
          class="noUi-target noUi-ltr noUi-horizontal relative"
          style="width: 575.48px; top: 153.1px; left: 75.096px"
        >
          <div class="noUi-base">
            <div class="noUi-connect" style="left: 0%; right: 25.77942%"></div>
            <div class="noUi-origin" style="left: 74.3206%">
              <div
                class="noUi-handle noUi-handle-lower"
                data-handle="0"
                tabindex="0"
                role="slider"
                aria-orientation="horizontal"
                aria-valuemin="0.0"
                aria-valuemax="100.0"
                aria-valuenow="92.2"
                aria-valuetext="1760880920.00"
                style="z-index: 4"
              >
                <div class="noUi-tooltip" style="display: none">2h 24m</div>
              </div>
            </div>
          </div>
        </div>
        <div
          class="flightReplayScrubberVerticalLine"
          style="top: 0px; left: 502.362px; height: 156.094px"
        ></div>
        <div
          class="flightReplayScrubberAltitude"
          style="top: 0px; left: 428.362px"
        >
          11,580 m
        </div>
        <div
          class="flightReplayScrubberGroundspeed"
          style="top: 0px; left: 504.362px"
        >
          870 km/h
        </div>
      </div>
    </div>
  </div>

  <!-- 主容器 -->
  <div class="mapcontainer">
    <!-- 航图区域 -->
    <div class="map-area">
      <div id="mapcc"></div>
    </div>
    <div
      class="absolute top-[11%] h-[5%] left-[50%] translate-x-[-50%] w-[45%]"
    >
      <img
        src="./assets/组 45@1x.png"
        alt="任务完成情况总览"
        class="w-full h-full"
      />
    </div>
    <!-- 左侧信息监控面板 -->
    <div class="side-panel" id="sidePanel">
      <div class="overflow-y-auto noscrollbar flex flex-col">
        <!-- 日期和总体完成度 -->
        <div class="">
          <img
            src="./assets/组 33@1x.png"
            alt="任务完成情况总览"
            class="w-full h-full"
          />
        </div>
      </div>

      <!-- 任务完成详情 -->
      <div class="flex-1 mt-2">
        <div class="space-y-3 max-h-full overflow-y-auto scrollbar-thin">
          <img
            src="./assets/组 151@1x.png"
            alt="任务完成情况总览"
            class="w-full h-full"
          />
        </div>
      </div>
      <div class="flex-1 mt-2">
        <div class="space-y-3 max-h-full overflow-y-auto scrollbar-thin">
          <img
            src="./assets/组 152@1x.png"
            alt="任务完成情况总览"
            class="w-full h-full"
          />
        </div>
      </div>
    </div>
    <!-- <div class="side-panel right-2 left-auto" id="sidePanel">
        <div class="overflow-y-auto noscrollbar flex flex-col">
          <div class="">
            <img src="./assets/组 41@1x.png" alt="任务完成情况总览" class="w-full h-full">
            </div>
          </div>
  
          <div
            class="flex-1 mt-6">
            <div class="space-y-3 max-h-full overflow-y-auto scrollbar-thin">
              <img src="./assets/组 40@1x.png" alt="任务完成情况总览" class="w-full h-full">
            </div>
          </div>
        </div> -->

    <div
      class="absolute right-[-19px] top-[30px] w-[20px] h-[100px] bg-[#34485982] rounded-r-xl"
    >
      <button class="panel-toggle" id="panelToggle">
        <svg
          viewBox="0 0 1024 1024"
          fill="#fff"
          version="1.1"
          xmlns="http://www.w3.org/2000/svg"
          p-id="1501"
          width="100"
          height="100"
        >
          <path
            d="M558.08 10.24a34.816 34.816 0 0 1 24.96 59.52L142.08 510.72l440.96 440.96c13.44 13.44 13.44 35.84 0 49.28a35.2 35.2 0 0 1-49.28 0L68.48 535.04a35.2 35.2 0 0 1 0-49.28L533.76 20.48c7.04-7.04 15.36-10.24 24.32-10.24z"
            p-id="1502"
          ></path>
          <path
            d="M931.2 10.24a34.816 34.816 0 0 1 24.96 59.52L515.2 510.72l440.96 440.96c13.44 13.44 13.44 35.84 0 49.28a35.2 35.2 0 0 1-49.28 0L440.96 535.04a35.328 35.328 0 0 1 0-49.92L906.24 19.84c7.04-6.4 16-9.6 24.96-9.6z"
            p-id="1503"
          ></path>
        </svg>
      </button>
    </div>
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
