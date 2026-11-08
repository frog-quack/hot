<!DOCTYPE html>
<html lang="zh-TW">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CalorieTrack AI - 個人熱量與體重追蹤助手</title>

  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- Vue 3 CDN -->
  <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
  <!-- Chart.js CDN -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <!-- FontAwesome Icons CDN -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <!-- Google Fonts: Inter & Noto Sans TC -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Noto+Sans+TC:wght@400;500;700&display=swap" rel="stylesheet">

  <script>
    tailwind.config = {
      darkMode: 'class',
      theme: {
        extend: {
          colors: {
            brand: {
              50: '#f0fdf4',
              100: '#dcfce7',
              500: '#22c55e',
              600: '#16a34a',
              700: '#15803d',
            }
          },
          fontFamily: {
            sans: ['Inter', 'Noto Sans TC', 'sans-serif'],
          }
        }
      }
    }
  </script>
  <style>
    [v-cloak] { display: none !important; }
    /* 隱藏滾動條但保持滾動 */
    .no-scrollbar::-webkit-scrollbar { display: none; }
    .no-scrollbar { -ms-overflow-style: none; scrollbar-width: none; }
  </style>
</head>
<body class="bg-slate-50 text-slate-800 dark:bg-slate-900 dark:text-slate-100 font-sans min-h-screen pb-20 md:pb-6">

  <div id="app" v-cloak class="max-w-md mx-auto md:max-w-4xl min-h-screen flex flex-col">

    <!-- 頂部導覽列 (Header) -->
    <header class="sticky top-0 z-30 bg-white/80 dark:bg-slate-800/80 backdrop-blur-md border-b border-slate-200 dark:border-slate-700 px-4 py-3 flex justify-between items-center">
      <div class="flex items-center gap-2">
        <div class="w-9 h-9 rounded-xl bg-brand-500 text-white flex items-center justify-center font-bold text-lg shadow-sm">
          <i class="fa-solid font-bold fa-fire-flame-curved"></i>
        </div>
        <div>
          <h1 class="font-bold text-base leading-tight">CalorieTrack AI</h1>
          <p class="text-[10px] text-slate-500 dark:text-slate-400">離線即用・AI 智慧記錄</p>
        </div>
      </div>
      <div class="flex items-center gap-2">
        <!-- API Key 設定按鈕 -->
        <button @click="showApiKeyModal = true" class="p-2 text-slate-600 dark:text-slate-300 hover:bg-slate-100 dark:hover:bg-slate-700 rounded-lg text-sm transition" title="設定 Gemini API Key">
          <i class="fa-solid fa-key" :class="apiKey ? 'text-brand-500' : 'text-slate-400'"></i>
        </button>
        <!-- 個人設定按鈕 -->
        <button @click="currentTab = 'profile'" class="p-2 text-slate-600 dark:text-slate-300 hover:bg-slate-100 dark:hover:bg-slate-700 rounded-lg text-sm transition" title="個人設定">
          <i class="fa-solid fa-user-gear"></i>
        </button>
      </div>
    </header>

    <!-- 主要內容區域 (Main Content) -->
    <main class="flex-1 p-4 space-y-5">

      <!-- ================= 頁籤 1: 每日總覽 (Dashboard & Today) ================= -->
      <section v-show="currentTab === 'dashboard'" class="space-y-4">
        
        <!-- 日期選擇器 -->
        <div class="flex justify-between items-center bg-white dark:bg-slate-800 p-3 rounded-2xl shadow-sm border border-slate-100 dark:border-slate-700">
          <button @click="changeDate(-1)" class="p-2 hover:bg-slate-100 dark:hover:bg-slate-700 rounded-xl text-slate-500">
            <i class="fa-solid fa-chevron-left"></i>
          </button>
          <div class="text-center font-semibold text-sm">
            <span>{{ selectedDateDisplay }}</span>
            <span v-if="isToday" class="ml-2 text-xs bg-brand-100 text-brand-700 dark:bg-brand-900/40 dark:text-brand-400 px-2 py-0.5 rounded-full font-normal">今天</span>
          </div>
          <button @click="changeDate(1)" class="p-2 hover:bg-slate-100 dark:hover:bg-slate-700 rounded-xl text-slate-500">
            <i class="fa-solid fa-chevron-right"></i>
          </button>
        </div>

        <!-- 每日熱量儀表板 Card -->
        <div class="bg-gradient-to-br from-slate-900 to-slate-800 text-white rounded-3xl p-5 shadow-xl relative overflow-hidden">
          <div class="absolute -right-6 -bottom-6 w-32 h-32 bg-brand-500/10 rounded-full blur-2xl"></div>

          <div class="flex justify-between items-start mb-4">
            <div>
              <span class="text-xs text-slate-400">尚可攝取熱量</span>
              <div class="text-3xl font-extrabold mt-1 tracking-tight">
                {{ remainingCalories }} <span class="text-sm font-normal text-slate-400">kcal</span>
              </div>
            </div>
            <div class="text-right">
              <span class="text-xs text-slate-400">每日目標 (TDEE)</span>
              <div class="text-sm font-semibold text-slate-200 mt-1">{{ Math.round(tdee) }} kcal</div>
            </div>
          </div>

          <!-- 熱量進度條 -->
          <div class="w-full bg-slate-700/60 rounded-full h-3 mb-4 overflow-hidden">
            <div class="h-full rounded-full transition-all duration-500" 
                 :class="calorieProgress > 100 ? 'bg-red-500' : 'bg-brand-500'"
                 :style="{ width: Math.min(calorieProgress, 100) + '%' }"></div>
          </div>

          <!-- 飲食與運動統計數據 Grid -->
          <div class="grid grid-cols-3 gap-2 text-center pt-2 border-t border-slate-700/60 text-xs">
            <div>
              <p class="text-slate-400">飲食攝取</p>
              <p class="font-bold text-sm text-emerald-400 mt-0.5">+{{ todayFoodCalories }}</p>
            </div>
            <div>
              <p class="text-slate-400">運動/步數消耗</p>
              <p class="font-bold text-sm text-amber-400 mt-0.5">-{{ todayBurnedCalories }}</p>
            </div>
            <div>
              <p class="text-slate-400">步數估算</p>
              <p class="font-bold text-sm text-sky-400 mt-0.5">{{ todaySteps }} 步</p>
            </div>
          </div>
        </div>

        <!-- 三大營養素進度條 (Macros) -->
        <div class="bg-white dark:bg-slate-800 rounded-2xl p-4 shadow-sm border border-slate-100 dark:border-slate-700 space-y-3">
          <h3 class="text-xs font-bold text-slate-400 uppercase tracking-wider">三大營養素達成率</h3>
          <div class="grid grid-cols-3 gap-3">
            <!-- 蛋白質 -->
            <div>
              <div class="flex justify-between text-xs mb-1">
                <span class="font-medium text-slate-600 dark:text-slate-300">蛋白質</span>
                <span class="text-slate-400">{{ todayMacros.protein }}g / {{ targetMacros.protein }}g</span>
              </div>
              <div class="w-full bg-slate-100 dark:bg-slate-700 h-2 rounded-full overflow-hidden">
                <div class="bg-blue-500 h-full rounded-full" :style="{ width: getMacroPercent(todayMacros.protein, targetMacros.protein) + '%' }"></div>
              </div>
            </div>
            <!-- 碳水化合物 -->
            <div>
              <div class="flex justify-between text-xs mb-1">
                <span class="font-medium text-slate-600 dark:text-slate-300">碳水</span>
                <span class="text-slate-400">{{ todayMacros.carbs }}g / {{ targetMacros.carbs }}g</span>
              </div>
              <div class="w-full bg-slate-100 dark:bg-slate-700 h-2 rounded-full overflow-hidden">
                <div class="bg-amber-500 h-full rounded-full" :style="{ width: getMacroPercent(todayMacros.carbs, targetMacros.carbs) + '%' }"></div>
              </div>
            </div>
            <!-- 脂肪 -->
            <div>
              <div class="flex justify-between text-xs mb-1">
                <span class="font-medium text-slate-600 dark:text-slate-300">脂肪</span>
                <span class="text-slate-400">{{ todayMacros.fat }}g / {{ targetMacros.fat }}g</span>
              </div>
              <div class="w-full bg-slate-100 dark:bg-slate-700 h-2 rounded-full overflow-hidden">
                <div class="bg-rose-500 h-full rounded-full" :style="{ width: getMacroPercent(todayMacros.fat, targetMacros.fat) + '%' }"></div>
              </div>
            </div>
          </div>
        </div>

        <!-- 快選捷徑按鈕 -->
        <div class="grid grid-cols-3 gap-3">
          <button @click="openAddFoodModal()" class="flex flex-col items-center justify-center p-3 bg-white dark:bg-slate-800 rounded-2xl border border-slate-100 dark:border-slate-700 shadow-sm hover:border-brand-500 transition group">
            <div class="w-10 h-10 rounded-full bg-emerald-50 dark:bg-emerald-950/40 text-emerald-600 dark:text-emerald-400 flex items-center justify-center text-lg mb-1 group-hover:scale-110 transition">
              <i class="fa-solid fa-utensils"></i>
            </div>
            <span class="text-xs font-medium">新增飲食</span>
          </button>

          <button @click="triggerAiCamera()" class="flex flex-col items-center justify-center p-3 bg-gradient-to-br from-brand-500 to-emerald-600 text-white rounded-2xl shadow-md hover:opacity-95 transition group">
            <div class="w-10 h-10 rounded-full bg-white/20 flex items-center justify-center text-lg mb-1 group-hover:scale-110 transition">
              <i class="fa-solid fa-camera"></i>
            </div>
            <span class="text-xs font-bold">AI 拍照辨識</span>
          </button>

          <button @click="openAddActivityModal()" class="flex flex-col items-center justify-center p-3 bg-white dark:bg-slate-800 rounded-2xl border border-slate-100 dark:border-slate-700 shadow-sm hover:border-brand-500 transition group">
            <div class="w-10 h-10 rounded-full bg-amber-50 dark:bg-amber-950/40 text-amber-600 dark:text-amber-400 flex items-center justify-center text-lg mb-1 group-hover:scale-110 transition">
              <i class="fa-solid fa-person-running"></i>
            </div>
            <span class="text-xs font-medium">新增運動/步數</span>
          </button>
        </div>

        <!-- 當日紀錄清單 -->
        <div class="bg-white dark:bg-slate-800 rounded-2xl p-4 shadow-sm border border-slate-100 dark:border-slate-700 space-y-3">
          <h3 class="text-sm font-bold flex justify-between items-center">
            <span>當日明細列表</span>
            <span class="text-xs text-slate-400 font-normal">點擊垃圾桶可刪除</span>
          </h3>

          <div v-if="todayLogs.length === 0" class="text-center py-8 text-slate-400 text-sm">
            <i class="fa-solid fa-plate-wheat text-3xl mb-2 opacity-40"></i>
            <p>今天還沒有任何紀錄喔！</p>
          </div>

          <div v-else class="space-y-2">
            <div v-for="log in todayLogs" :key="log.id" class="flex justify-between items-center p-3 bg-slate-50 dark:bg-slate-700/50 rounded-xl text-sm">
              <div class="flex items-center gap-3">
                <div class="w-8 h-8 rounded-lg flex items-center justify-center text-xs"
                     :class="log.type === 'food' ? 'bg-emerald-100 text-emerald-700 dark:bg-emerald-900/50 dark:text-emerald-300' : 'bg-amber-100 text-amber-700 dark:bg-amber-900/50 dark:text-amber-300'">
                  <i :class="log.type === 'food' ? 'fa-solid fa-bowl-food' : 'fa-solid fa-fire'"></i>
                </div>
                <div>
                  <p class="font-medium text-slate-800 dark:text-slate-100">{{ log.name }}</p>
                  <p class="text-[11px] text-slate-400">
                    <span v-if="log.type === 'food'">P:{{ log.protein || 0 }}g | C:{{ log.carbs || 0 }}g | F:{{ log.fat || 0 }}g</span>
                    <span v-else>{{ log.duration || 0 }} 分鐘 / {{ log.steps || 0 }} 步</span>
                  </p>
                </div>
              </div>
              <div class="flex items-center gap-3">
                <span class="font-bold" :class="log.type === 'food' ? 'text-emerald-600 dark:text-emerald-400' : 'text-amber-600 dark:text-amber-400'">
                  {{ log.type === 'food' ? '+' : '-' }}{{ log.calories }} kcal
                </span>
                <button @click="deleteLog(log.id)" class="text-slate-400 hover:text-red-500 p-1">
                  <i class="fa-solid fa-trash-can text-xs"></i>
                </button>
              </div>
            </div>
          </div>
        </div>

      </section>

      <!-- ================= 頁籤 2: 體重與趨勢圖表 (Analytics) ================= -->
      <section v-show="currentTab === 'analytics'" class="space-y-4">
        <!-- 快速記錄今日體重 -->
        <div class="bg-white dark:bg-slate-800 p-4 rounded-2xl shadow-sm border border-slate-100 dark:border-slate-700 flex justify-between items-center">
          <div>
            <h3 class="font-bold text-sm">記錄今日體重</h3>
            <p class="text-xs text-slate-400">上次紀錄: {{ latestWeight ? latestWeight + ' kg' : '無' }}</p>
          </div>
          <div class="flex gap-2">
            <input type="number" step="0.1" v-model="quickWeightInput" placeholder="kg" class="w-20 px-3 py-1.5 border border-slate-200 dark:border-slate-600 rounded-xl bg-slate-50 dark:bg-slate-700 text-sm focus:outline-none focus:ring-2 focus:ring-brand-500">
            <button @click="saveQuickWeight" class="px-4 py-1.5 bg-brand-500 hover:bg-brand-600 text-white font-medium text-sm rounded-xl transition">
              儲存
            </button>
          </div>
        </div>

        <!-- 體重變化趨勢圖表 -->
        <div class="bg-white dark:bg-slate-800 p-4 rounded-2xl shadow-sm border border-slate-100 dark:border-slate-700 space-y-3">
          <div class="flex justify-between items-center">
            <h3 class="font-bold text-sm">體重變化曲線 (kg)</h3>
            <!-- 時間跨度切換按鈕 -->
            <div class="flex text-xs bg-slate-100 dark:bg-slate-700 p-1 rounded-xl gap-1">
              <button v-for="days in [7, 30, 90]" :key="days" 
                      @click="chartRangeDays = days; updateWeightChart();"
                      :class="chartRangeDays === days ? 'bg-white dark:bg-slate-600 font-bold shadow-xs' : 'text-slate-500'"
                      class="px-2.5 py-1 rounded-lg transition">
                {{ days === 90 ? '近3個月' : days + '天' }}
              </button>
            </div>
          </div>
          <div class="h-56 relative">
            <canvas id="weightChart"></canvas>
          </div>
        </div>

        <!-- 每日熱量攝取 vs 消耗長條圖 -->
        <div class="bg-white dark:bg-slate-800 p-4 rounded-2xl shadow-sm border border-slate-100 dark:border-slate-700 space-y-3">
          <h3 class="font-bold text-sm">熱量平衡比對 (近 7 天)</h3>
          <div class="h-56 relative">
            <canvas id="calorieChart"></canvas>
          </div>
        </div>
      </section>

      <!-- ================= 頁籤 3: 個人檔案與 BMR/TDEE 計算 (Profile) ================= -->
      <section v-show="currentTab === 'profile'" class="space-y-4">
        <div class="bg-white dark:bg-slate-800 p-5 rounded-2xl shadow-sm border border-slate-100 dark:border-slate-700 space-y-4">
          <h2 class="text-base font-bold border-b border-slate-100 dark:border-slate-700 pb-2">個人身體資訊與目標</h2>
          
          <div class="grid grid-cols-2 gap-3">
            <div>
              <label class="block text-xs font-medium text-slate-500 mb-1">性別</label>
              <select v-model="userProfile.gender" class="w-full p-2.5 bg-slate-50 dark:bg-slate-700 border border-slate-200 dark:border-slate-600 rounded-xl text-sm">
                <option value="male">男性</option>
                <option value="female">女性</option>
              </select>
            </div>
            <div>
              <label class="block text-xs font-medium text-slate-500 mb-1">年齡 (歲)</label>
              <input type="number" v-model.number="userProfile.age" class="w-full p-2.5 bg-slate-50 dark:bg-slate-700 border border-slate-200 dark:border-slate-600 rounded-xl text-sm">
            </div>
            <div>
              <label class="block text-xs font-medium text-slate-500 mb-1">身高 (cm)</label>
              <input type="number" v-model.number="userProfile.height" class="w-full p-2.5 bg-slate-50 dark:bg-slate-700 border border-slate-200 dark:border-slate-600 rounded-xl text-sm">
            </div>
            <div>
              <label class="block text-xs font-medium text-slate-500 mb-1">目前體重 (kg)</label>
              <input type="number" step="0.1" v-model.number="userProfile.weight" class="w-full p-2.5 bg-slate-50 dark:bg-slate-700 border border-slate-200 dark:border-slate-600 rounded-xl text-sm">
            </div>
          </div>

          <div>
            <label class="block text-xs font-medium text-slate-500 mb-1">日常活動量級別</label>
            <select v-model.number="userProfile.activityLevel" class="w-full p-2.5 bg-slate-50 dark:bg-slate-700 border border-slate-200 dark:border-slate-600 rounded-xl text-sm">
              <option value="1.2">久坐 / 無規律運動 (BMR x 1.2)</option>
              <option value="1.375">輕度活動 (每週運動 1-3 天, BMR x 1.375)</option>
              <option value="1.55">中度活動 (每週運動 3-5 天, BMR x 1.55)</option>
              <option value="1.725">高度活動 (每週運動 6-7 天, BMR x 1.725)</option>
              <option value="1.9">極高強度 (專業運動員/重體力勞動, BMR x 1.9)</option>
            </select>
          </div>

          <div>
            <label class="block text-xs font-medium text-slate-500 mb-1">個人目標</label>
            <select v-model="userProfile.goal" class="w-full p-2.5 bg-slate-50 dark:bg-slate-700 border border-slate-200 dark:border-slate-600 rounded-xl text-sm">
              <option value="maintain">維持體重</option>
              <option value="lose">溫和減重 (-300 kcal/日)</option>
              <option value="gain">增肌增重 (+300 kcal/日)</option>
            </select>
          </div>

          <!-- BMR / TDEE 即時試算結果 -->
          <div class="bg-brand-50 dark:bg-brand-950/40 p-4 rounded-xl border border-brand-100 dark:border-brand-900/60 text-xs space-y-1">
            <div class="flex justify-between">
              <span class="text-slate-600 dark:text-slate-400">基礎代謝率 (BMR):</span>
              <span class="font-bold text-slate-800 dark:text-slate-200">{{ Math.round(bmr) }} kcal</span>
            </div>
            <div class="flex justify-between">
              <span class="text-slate-600 dark:text-slate-400">每日總熱量消耗 (TDEE):</span>
              <span class="font-bold text-brand-600 dark:text-brand-400 text-sm">{{ Math.round(tdee) }} kcal</span>
            </div>
          </div>

          <button @click="saveProfile" class="w-full py-3 bg-brand-500 hover:bg-brand-600 text-white font-bold rounded-xl shadow-sm transition">
            更新個人資料
          </button>
        </div>
      </section>

    </main>

    <!-- 底部導覽 Tab Bar (Mobile Bottom Nav) -->
    <nav class="fixed bottom-0 left-0 right-0 z-30 bg-white dark:bg-slate-800 border-t border-slate-200 dark:border-slate-700 max-w-md mx-auto md:max-w-4xl px-6 py-2 flex justify-around">
      <button @click="currentTab = 'dashboard'" :class="currentTab === 'dashboard' ? 'text-brand-500 font-bold' : 'text-slate-400'" class="flex flex-col items-center gap-1 text-xs transition">
        <i class="fa-solid fa-house-chimney text-lg"></i>
        <span>今日熱量</span>
      </button>
      <button @click="currentTab = 'analytics'; renderCharts();" :class="currentTab === 'analytics' ? 'text-brand-500 font-bold' : 'text-slate-400'" class="flex flex-col items-center gap-1 text-xs transition">
        <i class="fa-solid fa-chart-line text-lg"></i>
        <span>體重與趨勢</span>
      </button>
      <button @click="currentTab = 'profile'" :class="currentTab === 'profile' ? 'text-brand-500 font-bold' : 'text-slate-400'" class="flex flex-col items-center gap-1 text-xs transition">
        <i class="fa-solid fa-sliders text-lg"></i>
        <span>代謝設定</span>
      </button>
    </nav>

    <!-- ================= 彈出視窗：新增飲食 Modal ================= -->
    <div v-if="showAddFoodModal" class="fixed inset-0 z-50 bg-slate-900/60 backdrop-blur-xs flex items-center justify-center p-4">
      <div class="bg-white dark:bg-slate-800 rounded-3xl max-w-md w-full p-5 space-y-4 shadow-2xl">
        <div class="flex justify-between items-center">
          <h3 class="font-bold text-base">新增飲食紀錄</h3>
          <button @click="showAddFoodModal = false" class="text-slate-400 hover:text-slate-600"><i class="fa-solid fa-xmark text-lg"></i></button>
        </div>

        <!-- 搜尋常見食物快選 -->
        <div>
          <input type="text" v-model="foodSearchQuery" placeholder="搜尋常見食物 (例如: 雞胸肉, 便當)..." class="w-full p-2.5 bg-slate-50 dark:bg-slate-700 border border-slate-200 dark:border-slate-600 rounded-xl text-sm">
          <div v-if="filteredPresetFoods.length > 0" class="flex gap-1.5 overflow-x-auto no-scrollbar py-2">
            <button v-for="item in filteredPresetFoods" :key="item.name" @click="selectPresetFood(item)" class="whitespace-nowrap px-3 py-1 bg-slate-100 dark:bg-slate-700 hover:bg-brand-50 dark:hover:bg-brand-950/50 text-xs rounded-full border border-slate-200 dark:border-slate-600">
              {{ item.name }} ({{ item.calories }}k)
            </button>
          </div>
        </div>

        <!-- 手動輸入表單 -->
        <div class="space-y-3">
          <div>
            <label class="block text-xs font-medium text-slate-500 mb-1">食物名稱</label>
            <input type="text" v-model="foodForm.name" placeholder="例如：台式牛肉麵" class="w-full p-2.5 bg-slate-50 dark:bg-slate-700 border border-slate-200 dark:border-slate-600 rounded-xl text-sm">
          </div>
          <div class="grid grid-cols-2 gap-3">
            <div>
              <label class="block text-xs font-medium text-slate-500 mb-1">總熱量 (kcal)</label>
              <input type="number" v-model.number="foodForm.calories" class="w-full p-2.5 bg-slate-50 dark:bg-slate-700 border border-slate-200 dark:border-slate-600 rounded-xl text-sm">
            </div>
            <div>
              <label class="block text-xs font-medium text-slate-500 mb-1">蛋白質 (g)</label>
              <input type="number" v-model.number="foodForm.protein" class="w-full p-2.5 bg-slate-50 dark:bg-slate-700 border border-slate-200 dark:border-slate-600 rounded-xl text-sm">
            </div>
            <div>
              <label class="block text-xs font-medium text-slate-500 mb-1">碳水化合物 (g)</label>
              <input type="number" v-model.number="foodForm.carbs" class="w-full p-2.5 bg-slate-50 dark:bg-slate-700 border border-slate-200 dark:border-slate-600 rounded-xl text-sm">
            </div>
            <div>
              <label class="block text-xs font-medium text-slate-500 mb-1">脂肪 (g)</label>
              <input type="number" v-model.number="foodForm.fat" class="w-full p-2.5 bg-slate-50 dark:bg-slate-700 border border-slate-200 dark:border-slate-600 rounded-xl text-sm">
            </div>
          </div>
        </div>

        <button @click="saveFoodLog" class="w-full py-3 bg-brand-500 hover:bg-brand-600 text-white font-bold rounded-xl transition">
          確認新增飲食
        </button>
      </div>
    </div>

    <!-- ================= 彈出視窗：新增運動/步數 Modal ================= -->
    <div v-if="showAddActivityModal" class="fixed inset-0 z-50 bg-slate-900/60 backdrop-blur-xs flex items-center justify-center p-4">
      <div class="bg-white dark:bg-slate-800 rounded-3xl max-w-md w-full p-5 space-y-4 shadow-2xl">
        <div class="flex justify-between items-center">
          <h3 class="font-bold text-base">新增運動與步數消耗</h3>
          <button @click="showAddActivityModal = false" class="text-slate-400 hover:text-slate-600"><i class="fa-solid fa-xmark text-lg"></i></button>
        </div>

        <!-- 分頁切換: 運動項目 or 步數記錄 -->
        <div class="flex border-b border-slate-200 dark:border-slate-700 text-sm">
          <button @click="activityTab = 'exercise'" :class="activityTab === 'exercise' ? 'border-b-2 border-brand-500 font-bold text-brand-600' : 'text-slate-400'" class="flex-1 py-2 text-center">
            特定運動
          </button>
          <button @click="activityTab = 'steps'" :class="activityTab === 'steps' ? 'border-b-2 border-brand-500 font-bold text-brand-600' : 'text-slate-400'" class="flex-1 py-2 text-center">
            今日步數
          </button>
        </div>

        <!-- 1. 特定運動 -->
        <div v-if="activityTab === 'exercise'" class="space-y-3">
          <div>
            <label class="block text-xs font-medium text-slate-500 mb-1">選擇運動種類</label>
            <select v-model="activityForm.selectedPreset" @change="onPresetExerciseChange" class="w-full p-2.5 bg-slate-50 dark:bg-slate-700 border border-slate-200 dark:border-slate-600 rounded-xl text-sm">
              <option v-for="ex in presetExercises" :key="ex.name" :value="ex">{{ ex.name }} (約 {{ ex.cpm }} kcal/分鐘)</option>
            </select>
          </div>
          <div>
            <label class="block text-xs font-medium text-slate-500 mb-1">運動持續時間 (分鐘)</label>
            <input type="number" v-model.number="activityForm.duration" @input="calculateExerciseCalories" class="w-full p-2.5 bg-slate-50 dark:bg-slate-700 border border-slate-200 dark:border-slate-600 rounded-xl text-sm">
          </div>
          <div>
            <label class="block text-xs font-medium text-slate-500 mb-1">預估消耗熱量 (kcal)</label>
            <input type="number" v-model.number="activityForm.calories" class="w-full p-2.5 bg-slate-50 dark:bg-slate-700 border border-slate-200 dark:border-slate-600 rounded-xl text-sm">
          </div>
          <button @click="saveActivityLog" class="w-full py-3 bg-amber-500 hover:bg-amber-600 text-white font-bold rounded-xl transition">
            儲存運動紀錄
          </button>
        </div>

        <!-- 2. 步數輸入 -->
        <div v-if="activityTab === 'steps'" class="space-y-3">
          <div>
            <label class="block text-xs font-medium text-slate-500 mb-1">今日總步數</label>
            <input type="number" v-model.number="stepsInput" placeholder="例如: 8000" class="w-full p-2.5 bg-slate-50 dark:bg-slate-700 border border-slate-200 dark:border-slate-600 rounded-xl text-sm">
            <p class="text-[11px] text-slate-400 mt-1">※ 每 1000 步約可消耗 35~40 kcal (依個人體重試算)</p>
          </div>
          <button @click="saveStepsLog" class="w-full py-3 bg-sky-500 hover:bg-sky-600 text-white font-bold rounded-xl transition">
            更新步數熱量
          </button>
        </div>

      </div>
    </div>

    <!-- ================= 彈出視窗：AI 拍照辨識 Modal ================= -->
    <div v-if="showAiCameraModal" class="fixed inset-0 z-50 bg-slate-900/60 backdrop-blur-xs flex items-center justify-center p-4">
      <div class="bg-white dark:bg-slate-800 rounded-3xl max-w-md w-full p-5 space-y-4 shadow-2xl">
        <div class="flex justify-between items-center">
          <h3 class="font-bold text-base flex items-center gap-2">
            <i class="fa-solid fa-wand-magic-sparkles text-brand-500"></i> AI 食物拍照估算
          </h3>
          <button @click="showAiCameraModal = false" class="text-slate-400 hover:text-slate-600"><i class="fa-solid fa-xmark text-lg"></i></button>
        </div>

        <!-- 未填寫 Key 提示 -->
        <div v-if="!apiKey" class="p-3 bg-amber-50 dark:bg-amber-950/40 border border-amber-200 dark:border-amber-800 rounded-xl text-xs text-amber-700 dark:text-amber-300">
          <i class="fa-solid fa-circle-info mr-1"></i> 請點擊右上角鑰匙圖示設定 Gemini API Key 才能開啟即時拍照辨識喔！
        </div>

        <!-- 圖片上傳區塊 -->
        <div class="border-2 border-dashed border-slate-200 dark:border-slate-700 rounded-2xl p-4 text-center cursor-pointer hover:border-brand-500 transition" @click="triggerFileInput">
          <input type="file" ref="fileInput" accept="image/*" class="hidden" @change="handleImageUpload">
          <div v-if="!uploadedImage" class="py-6 space-y-2">
            <i class="fa-solid fa-cloud-arrow-up text-3xl text-slate-400"></i>
            <p class="text-xs text-slate-500">點擊上傳或使用手機相機拍攝餐點圖片</p>
          </div>
          <img v-else :src="uploadedImage" class="max-h-48 mx-auto rounded-xl object-cover shadow-sm">
        </div>

        <!-- AI 分析狀態 -->
        <div v-if="isAnalyzing" class="text-center py-4 space-y-2">
          <i class="fa-solid fa-spinner fa-spin text-2xl text-brand-500"></i>
          <p class="text-xs text-slate-500">AI 正在辨識您的餐點並估算營養價值...</p>
        </div>

        <!-- 辨識結果與修改 -->
        <div v-if="aiResult && !isAnalyzing" class="bg-slate-50 dark:bg-slate-700/50 p-3 rounded-2xl space-y-2 text-xs">
          <div class="font-bold text-slate-800 dark:text-slate-200 text-sm flex justify-between">
            <span>{{ aiResult.name }}</span>
            <span class="text-brand-600 dark:text-brand-400">{{ aiResult.calories }} kcal</span>
          </div>
          <p class="text-slate-500">{{ aiResult.description }}</p>
          <div class="grid grid-cols-3 gap-1 text-center font-medium pt-1">
            <div class="bg-white dark:bg-slate-600 p-1.5 rounded-lg">蛋白質: {{ aiResult.protein }}g</div>
            <div class="bg-white dark:bg-slate-600 p-1.5 rounded-lg">碳水: {{ aiResult.carbs }}g</div>
            <div class="bg-white dark:bg-slate-600 p-1.5 rounded-lg">脂肪: {{ aiResult.fat }}g</div>
          </div>
        </div>

        <button v-if="aiResult && !isAnalyzing" @click="applyAiResult" class="w-full py-3 bg-brand-500 hover:bg-brand-600 text-white font-bold rounded-xl transition">
          直接帶入並記錄
        </button>
      </div>
    </div>

    <!-- ================= 彈出視窗：Gemini API Key 設定 ================= -->
    <div v-if="showApiKeyModal" class="fixed inset-0 z-50 bg-slate-900/60 backdrop-blur-xs flex items-center justify-center p-4">
      <div class="bg-white dark:bg-slate-800 rounded-3xl max-w-md w-full p-5 space-y-4 shadow-2xl">
        <div class="flex justify-between items-center">
          <h3 class="font-bold text-base">設定 Gemini API Key</h3>
          <button @click="showApiKeyModal = false" class="text-slate-400 hover:text-slate-600"><i class="fa-solid fa-xmark text-lg"></i></button>
        </div>
        <p class="text-xs text-slate-500">本應用程式免費且零後端，您的 API Key 將僅安全保存在本機裝置 LocalStorage 中。</p>
        <div>
          <input type="password" v-model="tempApiKey" placeholder="貼上 AI Studio 發行的 Gemini API Key" class="w-full p-2.5 bg-slate-50 dark:bg-slate-700 border border-slate-200 dark:border-slate-600 rounded-xl text-sm">
        </div>
        <div class="flex gap-2">
          <button @click="saveApiKey" class="flex-1 py-2.5 bg-brand-500 hover:bg-brand-600 text-white font-bold text-sm rounded-xl transition">
            儲存 Key
          </button>
          <button @click="tempApiKey = ''; saveApiKey();" class="px-3 py-2.5 bg-slate-200 dark:bg-slate-700 text-slate-600 dark:text-slate-300 text-sm rounded-xl">
            清除
          </button>
        </div>
      </div>
    </div>

  </div>

  <script>
    const { createApp, ref, computed, onMounted, watch, nextTick } = Vue;

    createApp({
      setup() {
        // --- 狀態定義 ---
        const currentTab = ref('dashboard');
        const showAddFoodModal = ref(false);
        const showAddActivityModal = ref(false);
        const showAiCameraModal = ref(false);
        const showApiKeyModal = ref(false);
        const activityTab = ref('exercise');

        // 日期選擇 (預設今日: YYYY-MM-DD)
        const selectedDate = ref(new Date().toISOString().split('T')[0]);
        const quickWeightInput = ref('');

        // 圖表選取天數 (7, 30, 90)
        const chartRangeDays = ref(7);

        // API Key
        const apiKey = ref(localStorage.getItem('gemini_api_key') || '');
        const tempApiKey = ref(apiKey.value);

        // 個人基本資料設定 (LocalStorage 持久化)
        const userProfile = ref(JSON.parse(localStorage.getItem('user_profile')) || {
          gender: 'male',
          age: 28,
          height: 175,
          weight: 70,
          activityLevel: 1.375,
          goal: 'maintain' // maintain, lose, gain
        });

        // 本地數據紀錄結構: { '2026-03-30': [ { id, type: 'food'|'activity', name, calories, protein, carbs, fat, steps, duration } ] }
        const dailyLogs = ref(JSON.parse(localStorage.getItem('daily_logs')) || {});
        // 體重歷史紀錄: [ { date: '2026-03-30', weight: 70.2 } ]
        const weightLogs = ref(JSON.parse(localStorage.getItem('weight_logs')) || []);

        // 表單綁定變數
        const foodForm = ref({ name: '', calories: 0, protein: 0, carbs: 0, fat: 0 });
        const foodSearchQuery = ref('');
        const activityForm = ref({ selectedPreset: null, duration: 30, calories: 150 });
        const stepsInput = ref(0);

        // AI 辨識變數
        const uploadedImage = ref(null);
        const isAnalyzing = ref(false);
        const aiResult = ref(null);

        // 預設常見在地料理快選選單
        const presetFoods = [
          { name: '雞胸肉 (100g)', calories: 165, protein: 31, carbs: 0, fat: 3.6 },
          { name: '白飯 (一碗 200g)', calories: 280, protein: 6, carbs: 60, fat: 1 },
          { name: '台式排骨便當', calories: 750, protein: 28, carbs: 90, fat: 30 },
          { name: '無糖豆漿 (400ml)', calories: 140, protein: 14, carbs: 7, fat: 6 },
          { name: '地瓜 (中等 150g)', calories: 180, protein: 2.5, carbs: 41, fat: 0.3 },
          { name: '美式咖啡', calories: 10, protein: 0.5, carbs: 1, fat: 0 },
        ];

        // 預設常見運動清單 (cpm = calories per minute)
        const presetExercises = [
          { name: '慢跑 / 跑步 (8km/h)', cpm: 8.5 },
          { name: '網球 (對牆/自主練習)', cpm: 4.5 },
          { name: '網球 (標準單/雙打比賽)', cpm: 7.0 },
          { name: '輕度伸展 / 靜態拉筋', cpm: 2.5 },
          { name: '健走 / 散步', cpm: 4.0 },
          { name: '重訓 / 健身', cpm: 5.5 },
          { name: '騎單車 (中速)', cpm: 6.5 },
          { name: '游泳 (蛙式)', cpm: 9.0 },
          { name: '瑜伽 / 伸展', cpm: 3.0 }
        ];

        // --- BMR / TDEE 核心計算邏輯 (Mifflin-St Jeor 公式) ---
        const bmr = computed(() => {
          const { gender, weight, height, age } = userProfile.value;
          if (!weight || !height || !age) return 1500;
          if (gender === 'male') {
            return (10 * weight) + (6.25 * height) - (5 * age) + 5;
          } else {
            return (10 * weight) + (6.25 * height) - (5 * age) - 161;
          }
        });

        const tdee = computed(() => {
          let baseTdee = bmr.value * userProfile.value.activityLevel;
          if (userProfile.value.goal === 'lose') baseTdee -= 300;
          if (userProfile.value.goal === 'gain') baseTdee += 300;
          return baseTdee;
        });

        // 每日三大營養素建議目標 (蛋白質: 30%, 碳水: 45%, 脂肪: 25%)
        const targetMacros = computed(() => {
          const targetCal = tdee.value;
          return {
            protein: Math.round((targetCal * 0.30) / 4),
            carbs: Math.round((targetCal * 0.45) / 4),
            fat: Math.round((targetCal * 0.25) / 9)
          };
        });

        // 當天資料計算
        const todayLogs = computed(() => dailyLogs.value[selectedDate.value] || []);
        
        const todayFoodCalories = computed(() => {
          return todayLogs.value
            .filter(item => item.type === 'food')
            .reduce((sum, item) => sum + (item.calories || 0), 0);
        });

        const todayBurnedCalories = computed(() => {
          return todayLogs.value
            .filter(item => item.type === 'activity')
            .reduce((sum, item) => sum + (item.calories || 0), 0);
        });

        const todaySteps = computed(() => {
          const stepLog = todayLogs.value.find(item => item.isSteps);
          return stepLog ? stepLog.steps : 0;
        });

        const todayMacros = computed(() => {
          return todayLogs.value
            .filter(item => item.type === 'food')
            .reduce((acc, item) => {
              acc.protein += (item.protein || 0);
              acc.carbs += (item.carbs || 0);
              acc.fat += (item.fat || 0);
              return acc;
            }, { protein: 0, carbs: 0, fat: 0 });
        });

        const remainingCalories = computed(() => {
          return Math.round(tdee.value - todayFoodCalories.value + todayBurnedCalories.value);
        });

        const calorieProgress = computed(() => {
          return Math.round((todayFoodCalories.value / (tdee.value + todayBurnedCalories.value)) * 100) || 0;
        });

        const isToday = computed(() => {
          return selectedDate.value === new Date().toISOString().split('T')[0];
        });

        const selectedDateDisplay = computed(() => {
          const [y, m, d] = selectedDate.value.split('-');
          return `${m}月${d}日`;
        });

        const filteredPresetFoods = computed(() => {
          if (!foodSearchQuery.value) return presetFoods;
          return presetFoods.filter(f => f.name.includes(foodSearchQuery.value));
        });

        const latestWeight = computed(() => {
          if (weightLogs.value.length === 0) return userProfile.value.weight;
          const sorted = [...weightLogs.value].sort((a, b) => new Date(b.date) - new Date(a.date));
          return sorted[0].weight;
        });

        // --- 方法 handlers ---
        const changeDate = (days) => {
          const d = new Date(selectedDate.value);
          d.setDate(d.getDate() + days);
          selectedDate.value = d.toISOString().split('T')[0];
        };

        const getMacroPercent = (current, target) => {
          if (!target) return 0;
          return Math.min(Math.round((current / target) * 100), 100);
        };

        const openAddFoodModal = () => {
          foodForm.value = { name: '', calories: 0, protein: 0, carbs: 0, fat: 0 };
          showAddFoodModal.value = true;
        };

        const selectPresetFood = (item) => {
          foodForm.value = { ...item };
        };

        const saveFoodLog = () => {
          if (!foodForm.value.name || !foodForm.value.calories) return;
          const log = {
            id: Date.now(),
            type: 'food',
            ...foodForm.value
          };
          if (!dailyLogs.value[selectedDate.value]) {
            dailyLogs.value[selectedDate.value] = [];
          }
          dailyLogs.value[selectedDate.value].push(log);
          saveToLocalStorage();
          showAddFoodModal.value = false;
        };

        const openAddActivityModal = () => {
          activityForm.value.selectedPreset = presetExercises[0];
          onPresetExerciseChange();
          showAddActivityModal.value = true;
        };

        const onPresetExerciseChange = () => {
          if (activityForm.value.selectedPreset) {
            calculateExerciseCalories();
          }
        };

        const calculateExerciseCalories = () => {
          if (activityForm.value.selectedPreset) {
            const cpm = activityForm.value.selectedPreset.cpm;
            activityForm.value.calories = Math.round(cpm * (activityForm.value.duration || 0));
          }
        };

        const saveActivityLog = () => {
          const log = {
            id: Date.now(),
            type: 'activity',
            name: activityForm.value.selectedPreset.name,
            duration: activityForm.value.duration,
            calories: activityForm.value.calories
          };
          if (!dailyLogs.value[selectedDate.value]) {
            dailyLogs.value[selectedDate.value] = [];
          }
          dailyLogs.value[selectedDate.value].push(log);
          saveToLocalStorage();
          showAddActivityModal.value = false;
        };

        const saveStepsLog = () => {
          if (!stepsInput.value) return;
          // 粗估: 每 1000 步約消耗 38 kcal
          const cal = Math.round((stepsInput.value / 1000) * 38);
          
          if (!dailyLogs.value[selectedDate.value]) {
            dailyLogs.value[selectedDate.value] = [];
          }
          
          // 若已有步數紀錄則替換
          const existingIndex = dailyLogs.value[selectedDate.value].findIndex(i => i.isSteps);
          const stepLog = {
            id: existingIndex >= 0 ? dailyLogs.value[selectedDate.value][existingIndex].id : Date.now(),
            type: 'activity',
            name: `每日步數 (${stepsInput.value} 步)`,
            steps: stepsInput.value,
            calories: cal,
            isSteps: true
          };

          if (existingIndex >= 0) {
            dailyLogs.value[selectedDate.value][existingIndex] = stepLog;
          } else {
            dailyLogs.value[selectedDate.value].push(stepLog);
          }
          
          saveToLocalStorage();
          showAddActivityModal.value = false;
        };

        const deleteLog = (id) => {
          dailyLogs.value[selectedDate.value] = dailyLogs.value[selectedDate.value].filter(i => i.id !== id);
          saveToLocalStorage();
        };

        const saveQuickWeight = () => {
          if (!quickWeightInput.value) return;
          const w = parseFloat(quickWeightInput.value);
          userProfile.value.weight = w;
          
          // 更新體重紀錄列表
          const date = selectedDate.value;
          const idx = weightLogs.value.findIndex(item => item.date === date);
          if (idx >= 0) {
            weightLogs.value[idx].weight = w;
          } else {
            weightLogs.value.push({ date, weight: w });
          }
          
          saveToLocalStorage();
          quickWeightInput.value = '';
          updateWeightChart();
        };

        const saveProfile = () => {
          saveToLocalStorage();
          alert('個人資料設定已更新！');
        };

        const saveApiKey = () => {
          apiKey.value = tempApiKey.value;
          localStorage.setItem('gemini_api_key', apiKey.value);
          showApiKeyModal.value = false;
        };

        const saveToLocalStorage = () => {
          localStorage.setItem('user_profile', JSON.stringify(userProfile.value));
          localStorage.setItem('daily_logs', JSON.stringify(dailyLogs.value));
          localStorage.setItem('weight_logs', JSON.stringify(weightLogs.value));
        };

        // --- AI 食物拍照辨識 (Gemini Flash Vision API Integration) ---
        const triggerAiCamera = () => {
          showAiCameraModal.value = true;
          uploadedImage.value = null;
          aiResult.value = null;
        };

        const triggerFileInput = () => {
          const fileInput = document.querySelector('input[type="file"]');
          if (fileInput) fileInput.click();
        };

        const handleImageUpload = (event) => {
          const file = event.target.files[0];
          if (!file) return;

          const reader = new FileReader();
          reader.onload = (e) => {
            uploadedImage.value = e.target.result;
            analyzeImageWithGemini(e.target.result);
          };
          reader.readAsDataURL(file);
        };

        const analyzeImageWithGemini = async (base64Image) => {
          if (!apiKey.value) {
            alert('請先填寫 Gemini API Key 以啟用圖片辨識功能！');
            return;
          }

          isAnalyzing.value = true;
          aiResult.value = null;

          try {
            // 清理 Base64 前綴
            const base64Data = base64Image.split(',')[1];
            
            const prompt = `請辨識這張圖片中的餐點或食物，估算其熱量與三大營養素。
            請務必傳回嚴格格式的 JSON 物件，請勿包含 Markdown 標記，格式如下：
            {
              "name": "食物名稱(例如台式爌肉飯)",
              "calories": 650,
              "protein": 25,
              "carbs": 70,
              "fat": 28,
              "description": "簡短的熱量估算說明"
            }`;

            const url = `https://generativelanguage.googleapis.com/v1beta/models/gemini-3.1-flash-image:generateContent?key=${apiKey.value}`;

            const response = await fetch(url, {
              method: 'POST',
              headers: { 'Content-Type': 'application/json' },
              body: JSON.stringify({
                contents: [{
                  parts: [
                    { text: prompt },
                    { inlineData: { mimeType: 'image/jpeg', data: base64Data } }
                  ]
                }]
              })
            });

            const data = await response.json();
            const textResponse = data.candidates?.[0]?.content?.parts?.[0]?.text;
            
            // 解析 JSON
            const cleanJsonStr = textResponse.replace(/```json/g, '').replace(/```/g, '').trim();
            aiResult.value = JSON.parse(cleanJsonStr);

          } catch (err) {
            console.error('AI 辨識失敗:', err);
            alert('辨識過程發生錯誤，請確定 API Key 是否正確或圖片格式無誤。');
          } finally {
            isAnalyzing.value = false;
          }
        };

        const applyAiResult = () => {
          if (!aiResult.value) return;
          foodForm.value = {
            name: aiResult.value.name,
            calories: aiResult.value.calories,
            protein: aiResult.value.protein,
            carbs: aiResult.value.carbs,
            fat: aiResult.value.fat
          };
          saveFoodLog();
          showAiCameraModal.value = false;
        };

        // --- Chart.js 數據圖表繪製 ---
        let weightChartInstance = null;
        let calorieChartInstance = null;

        const renderCharts = () => {
          nextTick(() => {
            updateWeightChart();
            updateCalorieChart();
          });
        };

        const updateWeightChart = () => {
          const ctx = document.getElementById('weightChart');
          if (!ctx) return;

          // 整理過去 N 天的體重數據
          const days = chartRangeDays.value;
          const labels = [];
          const dataPoints = [];

          for (let i = days - 1; i >= 0; i--) {
            const d = new Date();
            d.setDate(d.getDate() - i);
            const dateStr = d.toISOString().split('T')[0];
            labels.push(`${d.getMonth()+1}/${d.getDate()}`);

            const match = weightLogs.value.find(w => w.date === dateStr);
            dataPoints.push(match ? match.weight : null);
          }

          if (weightChartInstance) weightChartInstance.destroy();

          weightChartInstance = new Chart(ctx, {
            type: 'line',
            data: {
              labels,
              datasets: [{
                label: '體重 (kg)',
                data: dataPoints,
                borderColor: '#22c55e',
                backgroundColor: 'rgba(34, 197, 94, 0.1)',
                fill: true,
                spanGaps: true,
                tension: 0.3,
                pointRadius: 4,
                pointBackgroundColor: '#22c55e'
              }]
            },
            options: {
              responsive: true,
              maintainAspectRatio: false,
              plugins: { legend: { display: false } },
              scales: {
                y: { beginAtZero: false }
              }
            }
          });
        };

        const updateCalorieChart = () => {
          const ctx = document.getElementById('calorieChart');
          if (!ctx) return;

          const labels = [];
          const intakeData = [];
          const burnData = [];

          // 固定呈現最近 7 天
          for (let i = 6; i >= 0; i--) {
            const d = new Date();
            d.setDate(d.getDate() - i);
            const dateStr = d.toISOString().split('T')[0];
            labels.push(`${d.getMonth()+1}/${d.getDate()}`);

            const logs = dailyLogs.value[dateStr] || [];
            const intake = logs.filter(l => l.type === 'food').reduce((sum, l) => sum + (l.calories || 0), 0);
            const burn = logs.filter(l => l.type === 'activity').reduce((sum, l) => sum + (l.calories || 0), 0);

            intakeData.push(intake);
            burnData.push(burn);
          }

          if (calorieChartInstance) calorieChartInstance.destroy();

          calorieChartInstance = new Chart(ctx, {
            type: 'bar',
            data: {
              labels,
              datasets: [
                { label: '攝取', data: intakeData, backgroundColor: '#10b981', borderRadius: 6 },
                { label: '運動/消耗', data: burnData, backgroundColor: '#f59e0b', borderRadius: 6 }
              ]
            },
            options: {
              responsive: true,
              maintainAspectRatio: false,
              plugins: { legend: { position: 'bottom' } }
            }
          });
        };

        // --- 初始化與掛載 ---
        onMounted(() => {
          // 初始化今日體重紀錄（若尚未填寫則代入個人檔案預設）
          const today = selectedDate.value;
          if (!weightLogs.value.some(w => w.date === today)) {
            weightLogs.value.push({ date: today, weight: userProfile.value.weight });
            saveToLocalStorage();
          }
          renderCharts();
        });

        return {
          currentTab,
          showAddFoodModal,
          showAddActivityModal,
          showAiCameraModal,
          showApiKeyModal,
          activityTab,
          selectedDate,
          selectedDateDisplay,
          isToday,
          userProfile,
          bmr,
          tdee,
          targetMacros,
          todayLogs,
          todayFoodCalories,
          todayBurnedCalories,
          todaySteps,
          todayMacros,
          remainingCalories,
          calorieProgress,
          quickWeightInput,
          latestWeight,
          foodForm,
          foodSearchQuery,
          filteredPresetFoods,
          presetExercises,
          activityForm,
          stepsInput,
          chartRangeDays,
          apiKey,
          tempApiKey,
          uploadedImage,
          isAnalyzing,
          aiResult,
          changeDate,
          getMacroPercent,
          openAddFoodModal,
          selectPresetFood,
          saveFoodLog,
          openAddActivityModal,
          onPresetExerciseChange,
          calculateExerciseCalories,
          saveActivityLog,
          saveStepsLog,
          deleteLog,
          saveQuickWeight,
          saveProfile,
          saveApiKey,
          triggerAiCamera,
          triggerFileInput,
          handleImageUpload,
          applyAiResult,
          updateWeightChart,
          renderCharts
        };
      }
    }).mount('#app');
  </script>
</body>
</html>
