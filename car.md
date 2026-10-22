<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>자율주행 자동차 사고 책임 토론 활동지</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts: Noto Sans KR -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <!-- Chart.js for Visualization -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <!-- html2pdf.js -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Noto Sans KR', 'sans-serif'],
                    },
                    colors: {
                        brand: {
                            50: '#f0f7ff',
                            100: '#e0effe',
                            500: '#3b82f6',
                            600: '#2563eb',
                            700: '#1d4ed8',
                            900: '#1e3a8a',
                        }
                    }
                }
            }
        }
    </script>
    
    <style>
        body {
            font-family: 'Noto Sans KR', sans-serif;
            background-color: #f8fafc;
            color: #1e293b;
        }

        .watermark-badge {
            position: absolute;
            top: 1.25rem;
            right: 1.25rem;
            background: linear-gradient(135deg, #6366f1 0%, #a855f7 100%);
            color: white;
            font-weight: 800;
            font-size: 1.1rem;
            padding: 0.4rem 1.2rem;
            border-radius: 9999px;
            box-shadow: 0 4px 12px rgba(99, 102, 241, 0.3);
            letter-spacing: 0.05em;
            z-index: 50;
        }

        .custom-scrollbar::-webkit-scrollbar {
            width: 6px;
        }
        .custom-scrollbar::-webkit-scrollbar-track {
            background: #f1f5f9;
        }
        .custom-scrollbar::-webkit-scrollbar-thumb {
            background: #cbd5e1;
            border-radius: 4px;
        }
    </style>
</head>
<body class="min-h-screen py-8 px-4 sm:px-6 lg:px-8">

    <!-- Main Outer Wrapper -->
    <div class="max-w-5xl mx-auto bg-white rounded-2xl shadow-xl border border-slate-200 overflow-hidden relative print-card">
        
        <!-- Right Top Teacher Badge -->
        <div class="watermark-badge select-none">
            <i class="fa-solid fa-graduation-cap mr-1.5"></i>리아t
        </div>

        <!-- Header Banner -->
        <header class="bg-gradient-to-r from-slate-900 via-indigo-950 to-slate-900 text-white p-6 sm:p-10 relative overflow-hidden">
            <div class="absolute -right-10 -bottom-10 w-40 h-40 bg-indigo-500/20 rounded-full blur-2xl"></div>
            <div class="relative z-10 max-w-3xl">
                <span class="inline-block px-3 py-1 bg-indigo-500/30 text-indigo-200 text-xs font-semibold rounded-full uppercase tracking-wider mb-3">
                    디지털 윤리 & 토론 워크북
                </span>
                <h1 class="text-2xl sm:text-4xl font-extrabold tracking-tight text-white mb-2">
                    🤖 자율주행자동차 사고 책임 토론
                </h1>
                <p class="text-slate-300 text-sm sm:text-base font-light">
                    "AI의 판단과 결과, 그 책임은 과연 누구에게 있는가?"
                </p>
                
                <!-- Student Info Inputs -->
                <div class="mt-6 grid grid-cols-2 gap-3 text-slate-800 text-sm">
                    <input type="text" id="studentId" placeholder="학번" class="px-3 py-1.5 rounded-lg border-0 focus:ring-2 focus:ring-indigo-400 bg-white/90 font-medium">
                    <input type="text" id="studentName" placeholder="이름" class="px-3 py-1.5 rounded-lg border-0 focus:ring-2 focus:ring-indigo-400 bg-white/90 font-medium">
                </div>
            </div>
        </header>

        <!-- Floating Action Controls for Students -->
        <div class="bg-slate-100 border-b border-slate-200 px-6 py-3 flex flex-wrap justify-between items-center gap-2 no-print">
            <div class="text-xs text-slate-500 font-medium flex items-center gap-1">
                <i class="fa-solid fa-circle-info text-indigo-500"></i>
                <span>작성 후 [제출 저장 & 링크 복사]를 누르면 시트에 저장되고 링크가 복사됩니다.</span>
            </div>
            <div class="flex items-center gap-2">
                <button onclick="saveAndCopyLink()" class="px-4 py-2 bg-emerald-600 hover:bg-emerald-700 text-white rounded-lg text-xs sm:text-sm font-bold transition flex items-center gap-2 shadow-sm cursor-pointer">
                    <i class="fa-solid fa-link text-base"></i> 제출 저장 & 링크 복사
                </button>
                <button onclick="exportToPDF()" class="px-3 py-2 bg-slate-600 hover:bg-slate-700 text-white rounded-lg text-xs font-bold transition flex items-center gap-1.5 shadow-sm cursor-pointer">
                    <i class="fa-solid fa-file-pdf"></i> PDF 저장
                </button>
            </div>
        </div>

        <!-- Main Form Body -->
        <div class="p-6 sm:p-10 space-y-10">

            <!-- SECTION 1: 사건 개요 -->
            <section class="bg-indigo-50/50 rounded-xl p-5 sm:p-7 border border-indigo-100 relative">
                <div class="flex items-center gap-3 mb-4">
                    <span class="flex items-center justify-center w-8 h-8 rounded-full bg-indigo-600 text-white font-bold text-sm">1</span>
                    <h2 class="text-xl font-bold text-slate-800">사건 개요 (2030년 도심 사고)</h2>
                </div>
                
                <div class="bg-white p-5 rounded-lg border border-indigo-100 shadow-sm space-y-4 text-sm text-slate-700 leading-relaxed">
                    <p class="font-medium text-slate-800">
                        🚨 <span class="underline decoration-indigo-300 underline-offset-4">2030년, A사의 자율주행자동차가 도심을 주행하고 있었습니다.</span>
                    </p>
                    <p class="text-base sm:text-lg font-bold text-slate-900 leading-snug bg-amber-50/60 p-4 rounded-xl border border-amber-200">
                        운전자는 자율주행 기능을 켜고 이동 중이었으며, 차량은 제한속도를 지키고 있었습니다. 
                        그런데 갑자기 도로에 공사 자재가 떨어졌고, 동시에 맞은편에서 보행자가 횡단보도로 진입했습니다.
                    </p>
                    <p class="bg-indigo-50/70 p-3.5 rounded-lg border-l-4 border-indigo-500 font-medium text-indigo-950 text-sm sm:text-base">
                        차량의 AI는 짧은 시간 안에 판단을 내려야 했고, 결과적으로 보행자와 충돌하는 사고가 발생했습니다.
                    </p>
                    
                    <div class="pt-2">
                        <h4 class="font-bold text-slate-900 mb-2 flex items-center gap-2">
                            <i class="fa-solid fa-magnifying-glass text-indigo-500"></i> 사고 조사 결과
                        </h4>
                        <ul class="grid grid-cols-1 sm:grid-cols-2 gap-2 text-xs sm:text-sm">
                            <li class="flex items-center gap-2 bg-slate-50 p-2 rounded border border-slate-200">
                                <i class="fa-solid fa-check text-emerald-500"></i> 자동차 하드웨어 이상 없음
                            </li>
                            <li class="flex items-center gap-2 bg-slate-50 p-2 rounded border border-slate-200">
                                <i class="fa-solid fa-check text-emerald-500"></i> SW 기존 테스트 정상 작동
                            </li>
                            <li class="flex items-center gap-2 bg-slate-50 p-2 rounded border border-slate-200">
                                <i class="fa-solid fa-check text-emerald-500"></i> 운전자의 정상적 기능 사용
                            </li>
                            <li class="flex items-center gap-2 bg-amber-50 p-2 rounded border border-amber-200 text-amber-800 font-semibold">
                                <i class="fa-solid fa-triangle-exclamation text-amber-500"></i> AI가 예상하지 못한 돌발 상황
                            </li>
                        </ul>
                    </div>
                </div>
            </section>

            <!-- SECTION 2: 역할 안내 -->
            <section class="space-y-4">
                <div class="flex items-center gap-3">
                    <span class="flex items-center justify-center w-8 h-8 rounded-full bg-indigo-600 text-white font-bold text-sm">2</span>
                    <h2 class="text-xl font-bold text-slate-800">토론 역할 안내</h2>
                </div>

                <div class="bg-indigo-50 border border-indigo-200 text-indigo-900 px-4 py-3 rounded-xl text-xs sm:text-sm font-semibold flex items-center gap-2.5">
                    <i class="fa-solid fa-users text-indigo-600 text-lg flex-shrink-0"></i>
                    <span>💡 모둠 내에서 역할을 1개씩 나누어 정하세요. (4인 모둠일 경우 '정부/윤리위원회' 역할을 제외하고 진행합니다.)</span>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-3 gap-4 text-xs sm:text-sm">
                    <div class="p-4 rounded-xl border border-blue-200 bg-blue-50/40 hover:shadow-md transition">
                        <div class="font-bold text-blue-900 text-base mb-1 flex items-center gap-2">
                            <i class="fa-solid fa-car text-blue-600"></i> 자동차 제조사
                        </div>
                        <p class="text-slate-600 leading-snug">
                            차체 안전성과 브랜드 신뢰도를 최우선시합니다. 기업 이미지 실추와 법적 책임을 최소화할 수 있는 안전한 시스템을 선호합니다.
                        </p>
                    </div>

                    <div class="p-4 rounded-xl border border-purple-200 bg-purple-50/40 hover:shadow-md transition">
                        <div class="font-bold text-purple-900 text-base mb-1 flex items-center gap-2">
                            <i class="fa-solid fa-code text-purple-600"></i> 소프트웨어 개발사
                        </div>
                        <p class="text-slate-600 leading-snug">
                            기술적 구현 가능성과 전체 피해 최소화에 집중합니다. 윤리적 기준을 프로그래밍 코드로 구현할 때의 현실적 한계를 주장합니다.
                        </p>
                    </div>

                    <div class="p-4 rounded-xl border border-emerald-200 bg-emerald-50/40 hover:shadow-md transition">
                        <div class="font-bold text-emerald-900 text-base mb-1 flex items-center gap-2">
                            <i class="fa-solid fa-user-shield text-emerald-600"></i> 차량 탑승자(구매자)
                        </div>
                        <p class="text-slate-600 leading-snug">
                            자기 보호 본능을 우선시합니다. "내 목숨을 담보로 남을 구하는 차는 아무도 사지 않을 것"이라며 소비자 권리를 강조합니다.
                        </p>
                    </div>

                    <div class="p-4 rounded-xl border border-rose-200 bg-rose-50/40 hover:shadow-md transition">
                        <div class="font-bold text-rose-900 text-base mb-1 flex items-center gap-2">
                            <i class="fa-solid fa-person-walking text-rose-600"></i> 보행자 / 시민 대표
                        </div>
                        <p class="text-slate-600 leading-snug">
                            보행자의 보상과 안전을 가장 중요하게 생각합니다. 도로 위 무고한 시민의 생명권 보호를 최우선 가치로 내세웁니다.
                        </p>
                    </div>

                    <div class="p-4 rounded-xl border border-amber-200 bg-amber-50/40 hover:shadow-md transition md:col-span-2">
                        <div class="font-bold text-amber-900 text-base mb-1 flex items-center gap-2">
                            <i class="fa-solid fa-scale-balanced text-amber-600"></i> 정부 / 윤리위원회 (5인 모둠용)
                        </div>
                        <p class="text-slate-600 leading-snug">
                            사회 전체의 안전과 명확한 법적 기준을 강조합니다. 특정 기업이나 개인의 이익보다 공공의 안녕 및 사회적 파급 효과를 고려합니다.
                        </p>
                    </div>
                </div>
            </section>

            <!-- SECTION 3: 역할 분석 -->
            <section class="space-y-6">
                <div class="flex items-center gap-3 border-b pb-3 border-slate-200">
                    <span class="flex items-center justify-center w-8 h-8 rounded-full bg-indigo-600 text-white font-bold text-sm">3</span>
                    <h2 class="text-xl font-bold text-slate-800">역할 분석</h2>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <div class="space-y-2">
                        <label class="block font-bold text-slate-800 text-sm">
                            Q1. 내가 맡은 역할은 누구인가요?
                        </label>
                        <select id="myRoleSelect" class="w-full p-3 rounded-lg border border-slate-300 focus:ring-2 focus:ring-indigo-500 bg-white font-medium text-slate-800">
                            <option value="">-- 역할을 선택하세요 --</option>
                            <option value="자동차 제조사">🚗 자동차 제조사</option>
                            <option value="소프트웨어 개발사">💻 소프트웨어 개발사</option>
                            <option value="차량 탑승자(구매자)">🛡️ 차량 탑승자 (구매자)</option>
                            <option value="보행자/시민 대표">🚶 보행자 / 시민 대표</option>
                            <option value="정부/윤리위원회">⚖️ 정부 / 윤리위원회</option>
                        </select>
                    </div>

                    <div class="space-y-2">
                        <label class="block font-bold text-slate-800 text-sm">
                            Q2. 내가 맡은 역할이 가장 중요하게 지켜야 하는 가치는 무엇인가요?
                        </label>
                        <input type="text" id="q2Value" placeholder="예: 브랜드 신뢰도, 탑승자 생명 보호, 사회 전체 법적 기준 등" class="w-full p-3 rounded-lg border border-slate-300 focus:ring-2 focus:ring-indigo-500 text-sm">
                    </div>
                </div>

                <div class="space-y-2">
                    <label class="block font-bold text-slate-800 text-sm">
                        Q3. 이번 사고에서 가장 큰 원인이나 책임을 제공한 주체(역할)는 누구라고 생각하나요? 그 이유는?
                    </label>
                    <textarea id="q3Cause" rows="3" placeholder="주체와 구체적인 이유를 논리적으로 적어보세요." class="w-full p-3 rounded-lg border border-slate-300 focus:ring-2 focus:ring-indigo-500 text-sm"></textarea>
                </div>

                <div class="space-y-3 bg-slate-50 p-5 rounded-xl border border-slate-200">
                    <label class="block font-bold text-slate-800 text-sm">
                        Q4. 자신의 역할 입장에서 각 역할마다 생각하는 <span class="text-indigo-600">책임 비율(%)</span>을 작성해보세요. (합계: <span id="initialTotal" class="font-extrabold text-rose-600 text-base">0</span>%)
                    </label>
                    
                    <div class="grid grid-cols-1 sm:grid-cols-5 gap-3 text-xs">
                        <div>
                            <span class="block font-semibold mb-1 text-slate-700">제조사</span>
                            <input type="number" min="0" max="100" id="initR1" value="0" oninput="calcInitialTotal()" class="w-full p-2 rounded border border-slate-300 text-center font-bold">
                        </div>
                        <div>
                            <span class="block font-semibold mb-1 text-slate-700">SW개발사</span>
                            <input type="number" min="0" max="100" id="initR2" value="0" oninput="calcInitialTotal()" class="w-full p-2 rounded border border-slate-300 text-center font-bold">
                        </div>
                        <div>
                            <span class="block font-semibold mb-1 text-slate-700">탑승자</span>
                            <input type="number" min="0" max="100" id="initR3" value="0" oninput="calcInitialTotal()" class="w-full p-2 rounded border border-slate-300 text-center font-bold">
                        </div>
                        <div>
                            <span class="block font-semibold mb-1 text-slate-700">보행자/도로관리</span>
                            <input type="number" min="0" max="100" id="initR4" value="0" oninput="calcInitialTotal()" class="w-full p-2 rounded border border-slate-300 text-center font-bold">
                        </div>
                        <div>
                            <span class="block font-semibold mb-1 text-slate-700">정부/지자체</span>
                            <input type="number" min="0" max="100" id="initR5" value="0" oninput="calcInitialTotal()" class="w-full p-2 rounded border border-slate-300 text-center font-bold">
                        </div>
                    </div>
                </div>

                <div class="space-y-2">
                    <label class="block font-bold text-slate-800 text-sm">
                        Q5. 다른 역할이 내가 맡은 역할을 비판한다면, 뭐라고 반론/대답할 수 있을까요?
                    </label>
                    <textarea id="q5Defense" rows="3" placeholder="예상되는 예상 비판과 이에 대한 내 역할의 방어 논리를 준비해봅시다." class="w-full p-3 rounded-lg border border-slate-300 focus:ring-2 focus:ring-indigo-500 text-sm"></textarea>
                </div>
            </section>

            <!-- SECTION 4: 공식 입장 정하기 -->
            <section class="space-y-4 bg-indigo-900 text-white p-6 sm:p-8 rounded-2xl shadow-md">
                <div class="flex items-center gap-3">
                    <span class="flex items-center justify-center w-8 h-8 rounded-full bg-white text-indigo-950 font-bold text-sm">4</span>
                    <h2 class="text-xl font-bold text-white">공식 입장 정하기</h2>
                </div>

                <div class="space-y-4 text-sm">
                    <div>
                        <label class="block font-semibold mb-2 text-indigo-200">
                            제 역할의 공식 입장은 아래와 같습니다:
                        </label>
                        <div class="flex flex-wrap items-center gap-2 text-base font-bold bg-white/10 p-4 rounded-xl border border-white/20">
                            <span>"우리 역할의 공식 입장은</span>
                            <input type="text" id="officialPosition" placeholder="한 문장으로 명확한 주장 작성" class="flex-1 min-w-[250px] p-2 rounded bg-white text-slate-900 font-medium text-sm focus:outline-none focus:ring-2 focus:ring-indigo-300">
                            <span>입니다."</span>
                        </div>
                    </div>

                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 pt-2">
                        <div class="space-y-1">
                            <label class="block font-semibold text-indigo-200 text-xs">📌 근거 1</label>
                            <textarea id="reason1" rows="3" placeholder="주장을 뒷받침할 구체적 근거 1" class="w-full p-3 rounded-lg text-slate-900 text-sm focus:outline-none"></textarea>
                        </div>
                        <div class="space-y-1">
                            <label class="block font-semibold text-indigo-200 text-xs">📌 근거 2</label>
                            <textarea id="reason2" rows="3" placeholder="주장을 뒷받침할 구체적 근거 2" class="w-full p-3 rounded-lg text-slate-900 text-sm focus:outline-none"></textarea>
                        </div>
                    </div>
                </div>
            </section>

            <!-- SECTION 5: 토론 진행 -->
            <section class="space-y-6">
                <div class="flex items-center gap-3 border-b pb-3 border-slate-200">
                    <span class="flex items-center justify-center w-8 h-8 rounded-full bg-indigo-600 text-white font-bold text-sm">5</span>
                    <h2 class="text-xl font-bold text-slate-800">토론 진행 (입장 발표 및 질의응답)</h2>
                </div>

                <div class="bg-slate-800 text-white p-5 sm:p-6 rounded-xl text-xs sm:text-sm shadow-sm space-y-4">
                    <div>
                        <div class="font-bold mb-3 text-indigo-300 flex items-center gap-2 text-sm sm:text-base">
                            <i class="fa-solid fa-list-ol"></i> 1분 입장 발표 순서
                        </div>
                        <div class="flex flex-wrap items-center gap-2 font-medium text-slate-200">
                            <span class="bg-rose-500/30 px-3 py-1.5 rounded-md border border-rose-400/30">1. 보행자/시민 대표</span>
                            <i class="fa-solid fa-chevron-right text-slate-500"></i>
                            <span class="bg-emerald-500/30 px-3 py-1.5 rounded-md border border-emerald-400/30">2. 탑승자</span>
                            <i class="fa-solid fa-chevron-right text-slate-500"></i>
                            <span class="bg-blue-500/30 px-3 py-1.5 rounded-md border border-blue-400/30">3. 자동차 제조사</span>
                            <i class="fa-solid fa-chevron-right text-slate-500"></i>
                            <span class="bg-purple-500/30 px-3 py-1.5 rounded-md border border-purple-400/30">4. SW 개발사</span>
                            <i class="fa-solid fa-chevron-right text-slate-500"></i>
                            <span class="bg-amber-500/30 px-3 py-1.5 rounded-md border border-amber-400/30">5. 정부/윤리위</span>
                        </div>
                    </div>

                    <div class="pt-3 border-t border-slate-700/80">
                        <div class="font-bold mb-2 text-amber-300 flex items-center gap-2 text-sm sm:text-base">
                            <i class="fa-solid fa-comments"></i> 서로 질문하기 규칙
                        </div>
                        <p class="text-slate-300 text-xs sm:text-sm leading-relaxed">
                            💡 <span class="font-bold text-white underline decoration-amber-400 underline-offset-4">질문 → 답변 구조</span>로 진행합니다. 무조건 1회 이상 질문하고 답변해야 합니다. (추가 질문 가능)
                        </p>
                    </div>
                </div>
            </section>

            <!-- SECTION 6: 함께 책임 비율 정하기 -->
            <section class="space-y-6">
                <div class="flex items-center gap-3 border-b pb-3 border-slate-200">
                    <span class="flex items-center justify-center w-8 h-8 rounded-full bg-indigo-600 text-white font-bold text-sm">6</span>
                    <h2 class="text-xl font-bold text-slate-800">모둠 합의: 함께 책임 비율 정하기 (총합 100%)</h2>
                </div>

                <p class="text-xs sm:text-sm text-slate-600">
                    토론 후 모둠원들과 협의하여 사고 책임 100%를 각 주체에게 분배하고 이유를 정리하세요.
                </p>

                <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center bg-slate-50 p-6 rounded-2xl border border-slate-200">
                    <div class="lg:col-span-7 space-y-4">
                        <div>
                            <div class="flex justify-between text-xs font-bold mb-1">
                                <span class="text-blue-700">자동차 제조사</span>
                                <span id="val1" class="text-blue-700 font-extrabold text-sm">20%</span>
                            </div>
                            <input type="range" id="slide1" min="0" max="100" value="20" oninput="updateChart()" onchange="updateChart()" class="w-full accent-blue-600">
                        </div>

                        <div>
                            <div class="flex justify-between text-xs font-bold mb-1">
                                <span class="text-purple-700">소프트웨어 개발사</span>
                                <span id="val2" class="text-purple-700 font-extrabold text-sm">20%</span>
                            </div>
                            <input type="range" id="slide2" min="0" max="100" value="20" oninput="updateChart()" onchange="updateChart()" class="w-full accent-purple-600">
                        </div>

                        <div>
                            <div class="flex justify-between text-xs font-bold mb-1">
                                <span class="text-emerald-700">차량 탑승자 (운전자)</span>
                                <span id="val3" class="text-emerald-700 font-extrabold text-sm">20%</span>
                            </div>
                            <input type="range" id="slide3" min="0" max="100" value="20" oninput="updateChart()" onchange="updateChart()" class="w-full accent-emerald-600">
                        </div>

                        <div>
                            <div class="flex justify-between text-xs font-bold mb-1">
                                <span class="text-rose-700">보행자 / 도로 관리 주체</span>
                                <span id="val4" class="text-rose-700 font-extrabold text-sm">20%</span>
                            </div>
                            <input type="range" id="slide4" min="0" max="100" value="20" oninput="updateChart()" onchange="updateChart()" class="w-full accent-rose-600">
                        </div>

                        <div>
                            <div class="flex justify-between text-xs font-bold mb-1">
                                <span class="text-amber-700">정부 / 윤리 제도</span>
                                <span id="val5" class="text-amber-700 font-extrabold text-sm">20%</span>
                            </div>
                            <input type="range" id="slide5" min="0" max="100" value="20" oninput="updateChart()" onchange="updateChart()" class="w-full accent-amber-600">
                        </div>

                        <div id="totalBadge" class="p-3 rounded-lg text-center font-bold text-sm bg-emerald-100 text-emerald-800 border border-emerald-300">
                            총합: <span id="totalPercent" class="font-extrabold text-emerald-600 text-base">100</span>% (정상적으로 100%가 설정되었습니다 👍)
                        </div>
                    </div>

                    <div class="lg:col-span-5 flex flex-col items-center justify-center p-4 bg-white rounded-xl shadow-sm border border-slate-200">
                        <div class="w-48 h-48 sm:w-56 sm:h-56 relative flex items-center justify-center">
                            <canvas id="ratioChart"></canvas>
                        </div>
                        <span class="text-xs text-slate-400 mt-2">최종 모둠 합의 책임 분포도</span>
                    </div>
                </div>

                <div class="space-y-2">
                    <label class="block font-bold text-slate-800 text-sm">
                        📝 이 책임 비율로 합의하게 된 주요 원인 및 근거 요약
                    </label>
                    <textarea id="ratioReason" rows="3" placeholder="모둠에서 이러한 책임 비율을 산정한 핵심 논리와 타협점을 서술하세요." class="w-full p-3 rounded-lg border border-slate-300 focus:ring-2 focus:ring-indigo-500 text-sm"></textarea>
                </div>
            </section>

            <!-- SECTION 7: 최종 협상 및 미래 원칙 수립 -->
            <section class="space-y-6">
                <div class="flex items-center gap-3 border-b pb-3 border-slate-200">
                    <span class="flex items-center justify-center w-8 h-8 rounded-full bg-indigo-600 text-white font-bold text-sm">7</span>
                    <h2 class="text-xl font-bold text-slate-800">최종 협상: 미래 자율주행 사고 책임 원칙 (3가지 이상)</h2>
                </div>

                <div class="bg-indigo-900 text-indigo-50 p-6 rounded-2xl border-l-8 border-indigo-400 text-base sm:text-lg font-extrabold leading-relaxed shadow-md">
                    "AI가 아무리 정확하게 판단하더라도, 그 판단의 결과에 대한 책임을 누가 질 것인가는 또 다른 문제입니다."
                </div>

                <div class="space-y-4">
                    <div class="p-4 bg-slate-50 rounded-xl border border-slate-200 space-y-2">
                        <div class="font-bold text-indigo-900 text-sm flex items-center gap-2">
                            <span class="w-5 h-5 rounded-full bg-indigo-600 text-white text-xs flex items-center justify-center">1</span>
                            원칙 1
                        </div>
                        <input type="text" id="principle1" placeholder="예: 제조사는 차량의 하드웨어 및 기본 안전성을 보장할 책임을 진다." class="w-full p-2.5 rounded-lg border border-slate-300 text-sm bg-white font-medium">
                    </div>

                    <div class="p-4 bg-slate-50 rounded-xl border border-slate-200 space-y-2">
                        <div class="font-bold text-indigo-900 text-sm flex items-center gap-2">
                            <span class="w-5 h-5 rounded-full bg-indigo-600 text-white text-xs flex items-center justify-center">2</span>
                            원칙 2
                        </div>
                        <input type="text" id="principle2" placeholder="예: 제조사는 차량의 하드웨어 및 기본 안전성을 보장할 책임을 진다." class="w-full p-2.5 rounded-lg border border-slate-300 text-sm bg-white font-medium">
                    </div>

                    <div class="p-4 bg-slate-50 rounded-xl border border-slate-200 space-y-2">
                        <div class="font-bold text-indigo-900 text-sm flex items-center gap-2">
                            <span class="w-5 h-5 rounded-full bg-indigo-600 text-white text-xs flex items-center justify-center">3</span>
                            원칙 3
                        </div>
                        <input type="text" id="principle3" placeholder="예: 제조사는 차량의 하드웨어 및 기본 안전성을 보장할 책임을 진다." class="w-full p-2.5 rounded-lg border border-slate-300 text-sm bg-white font-medium">
                    </div>
                </div>
            </section>

            <!-- SECTION 8: 종합 소감 -->
            <section class="space-y-3">
                <label class="block font-bold text-slate-800 text-sm">
                    ✨ 토론을 마치며 (나의 깨달음과 느낀 점)
                </label>
                <textarea id="finalReflection" rows="3" placeholder="기술의 발전과 윤리적 법적 책임을 연결하여 생각해보게 된 점을 작성하세요." class="w-full p-3 rounded-lg border border-slate-300 focus:ring-2 focus:ring-indigo-500 text-sm"></textarea>
            </section>

        </div>

        <!-- Footer -->
        <footer class="bg-slate-100 border-t border-slate-200 p-6 text-center text-xs text-slate-500">
            <p>자율주행 자동차 사고 책임 윤리 토론 워크북 &bull; 리아t</p>
        </footer>
    </div>

    <!-- Toast Notification Container -->
    <div id="toast" class="fixed bottom-5 right-5 bg-slate-900 text-white px-4 py-3 rounded-xl shadow-2xl text-xs sm:text-sm font-semibold opacity-0 transition-opacity duration-300 pointer-events-none z-50 flex items-center gap-2">
        <i class="fa-solid fa-circle-check text-emerald-400"></i>
        <span id="toastMsg">내용이 저장되었습니다!</span>
    </div>

    <script>
        // 🚨 1단계에서 발급받은 구글 앱스 스크립트 웹 앱 URL을 아래 따옴표 안에 꼭 넣으세요!
        const GAS_URL = "https://script.google.com/macros/s/AKfycbw12_9T6uKtwumIMLceqdWsLQdOBd_9hY8ujjRN7FgskEAZuD8hvMcGHjQXnoHg_6J3-Q/exec";

        let myChart = null;

        window.onload = function() {
            initChart();

            // URL 파라미터에 id가 존재하는지 확인 (예: ?id=id_12345)
            const urlParams = new URLSearchParams(window.location.search);
            const savedId = urlParams.get('id');

            if (savedId && GAS_URL && GAS_URL !== "YOUR_GAS_URL_HERE") {
                loadDataFromGAS(savedId);
            } else {
                loadSavedData();
                calcInitialTotal();
                updateChart();
            }
        };

        function getVal(id) {
            return document.getElementById(id)?.value || '';
        }

        function setVal(id, val) {
            const el = document.getElementById(id);
            if (el && val !== undefined) el.value = val;
        }

        // 구글 스프레드시트에 저장 및 패들렛 제출용 링크 복사
        async function saveAndCopyLink() {
            if (!GAS_URL || GAS_URL === "YOUR_GAS_URL_HERE") {
                alert('구글 앱스 스크립트 URL이 설정되지 않았습니다. 코드 상단의 GAS_URL을 입력해 주세요.');
                return;
            }

            const studentId = getVal('studentId').trim();
            const studentName = getVal('studentName').trim();

            if (!studentId || !studentName) {
                alert('학번과 이름을 먼저 입력해 주세요.');
                return;
            }

            const data = {
                studentId: studentId,
                studentName: studentName,
                myRoleSelect: getVal('myRoleSelect'),
                q2Value: getVal('q2Value'),
                q3Cause: getVal('q3Cause'),
                initR1: getVal('initR1'),
                initR2: getVal('initR2'),
                initR3: getVal('initR3'),
                initR4: getVal('initR4'),
                initR5: getVal('initR5'),
                q5Defense: getVal('q5Defense'),
                officialPosition: getVal('officialPosition'),
                reason1: getVal('reason1'),
                reason2: getVal('reason2'),
                slide1: getVal('slide1'),
                slide2: getVal('slide2'),
                slide3: getVal('slide3'),
                slide4: getVal('slide4'),
                slide5: getVal('slide5'),
                ratioReason: getVal('ratioReason'),
                principle1: getVal('principle1'),
                principle2: getVal('principle2'),
                principle3: getVal('principle3'),
                finalReflection: getVal('finalReflection')
            };

            showToast('스프레드시트에 저장 중입니다...');

            try {
                const response = await fetch(GAS_URL, {
                    method: 'POST',
                    body: JSON.stringify(data)
                });
                const res = await response.json();

                if (res.result === 'success') {
                    // 고유 id를 포함한 주소 생성
                    const baseUrl = window.location.origin + window.location.pathname;
                    const shareUrl = `${baseUrl}?id=${res.id}`;

                    // 클립보드에 클라이언트 링크 복사
                    if (navigator.clipboard && window.isSecureContext) {
                        await navigator.clipboard.writeText(shareUrl);
                    } else {
                        const textArea = document.createElement("textarea");
                        textArea.value = shareUrl;
                        document.body.appendChild(textArea);
                        textArea.select();
                        document.execCommand('copy');
                        document.body.removeChild(textArea);
                    }

                    alert(`✅ 구글 스프레드시트에 저장되었습니다!\n\n학생만의 제출 링크가 복사되었습니다.\n패들렛(Padlet)으로 이동하여 붙여넣기(Ctrl+V) 하세요!\n\n링크: ${shareUrl}`);
                    showToast('링크 복사 완료! 패들렛에 붙여넣으세요. 🔗');
                } else {
                    alert('저장 실패: ' + (res.error || '오류가 발생했습니다.'));
                }
            } catch (err) {
                console.error(err);
                alert('구글 스프레드시트 연동 중 통신 에러가 발생했습니다.');
            }
        }

        // URL 파라미터 id 기반으로 시트 데이터 불러오기
        async function loadDataFromGAS(id) {
            showToast('작성된 데이터를 불러오는 중입니다...');
            try {
                const response = await fetch(`${GAS_URL}?id=${encodeURIComponent(id)}`);
                const res = await response.json();

                if (res.result === 'success' && res.data) {
                    const d = res.data;
                    setVal('studentId', d.studentId);
                    setVal('studentName', d.studentName);
                    setVal('myRoleSelect', d.myRoleSelect);
                    setVal('q2Value', d.q2Value);
                    setVal('q3Cause', d.q3Cause);
                    setVal('initR1', d.initR1);
                    setVal('initR2', d.initR2);
                    setVal('initR3', d.initR3);
                    setVal('initR4', d.initR4);
                    setVal('initR5', d.initR5);
                    setVal('q5Defense', d.q5Defense);
                    setVal('officialPosition', d.officialPosition);
                    setVal('reason1', d.reason1);
                    setVal('reason2', d.reason2);
                    setVal('slide1', d.slide1);
                    setVal('slide2', d.slide2);
                    setVal('slide3', d.slide3);
                    setVal('slide4', d.slide4);
                    setVal('slide5', d.slide5);
                    setVal('ratioReason', d.ratioReason);
                    setVal('principle1', d.principle1);
                    setVal('principle2', d.principle2);
                    setVal('principle3', d.principle3);
                    setVal('finalReflection', d.finalReflection);

                    calcInitialTotal();
                    updateChart();
                    showToast('저장된 데이터를 로드했습니다! 📖');
                } else {
                    alert('해당 ID의 저장 데이터를 찾을 수 없습니다.');
                }
            } catch (err) {
                console.error(err);
                showToast('데이터 로드 실패');
            }
        }

        function initChart() {
            try {
                const canvas = document.getElementById('ratioChart');
                if (!canvas) return;
                const ctx = canvas.getContext('2d');
                if (typeof Chart === 'undefined') return;
                
                myChart = new Chart(ctx, {
                    type: 'doughnut',
                    data: {
                        labels: ['제조사', 'SW개발사', '탑승자', '보행자/도로', '정부/윤리위'],
                        datasets: [{
                            data: [20, 20, 20, 20, 20],
                            backgroundColor: ['#2563eb', '#9333ea', '#059669', '#e11d48', '#d97706'],
                            borderWidth: 2,
                            borderColor: '#ffffff'
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false,
                        plugins: { legend: { display: false } },
                        cutout: '65%'
                    }
                });
            } catch (e) {
                console.error("차트 초기화 오류:", e);
            }
        }

        function updateChart() {
            const getNum = (id) => {
                const val = parseInt(getVal(id), 10);
                return isNaN(val) ? 0 : val;
            };

            const s1 = getNum('slide1');
            const s2 = getNum('slide2');
            const s3 = getNum('slide3');
            const s4 = getNum('slide4');
            const s5 = getNum('slide5');

            const setTxt = (id, txt) => {
                const el = document.getElementById(id);
                if (el) el.innerText = txt;
            };

            setTxt('val1', s1 + '%');
            setTxt('val2', s2 + '%');
            setTxt('val3', s3 + '%');
            setTxt('val4', s4 + '%');
            setTxt('val5', s5 + '%');

            const total = s1 + s2 + s3 + s4 + s5;
            const badgeEl = document.getElementById('totalBadge');

            if (badgeEl) {
                if (total === 100) {
                    badgeEl.className = "p-3 rounded-lg text-center font-bold text-sm bg-emerald-100 text-emerald-800 border border-emerald-300";
                    badgeEl.innerHTML = `총합: <span id="totalPercent" class="font-extrabold text-emerald-600 text-base">100</span>% (정상적으로 100%가 설정되었습니다 👍)`;
                } else {
                    const diff = total - 100;
                    const diffStr = diff > 0 ? `+${diff}` : `${diff}`;
                    badgeEl.className = "p-3 rounded-lg text-center font-bold text-sm bg-rose-100 text-rose-800 border border-rose-300";
                    badgeEl.innerHTML = `총합: <span id="totalPercent" class="font-extrabold text-rose-600 text-base">${total}</span>% (총합을 100%로 맞춰주세요! 현재 차이: ${diffStr}%)`;
                }
            }

            if (myChart && myChart.data && myChart.data.datasets && myChart.data.datasets[0]) {
                myChart.data.datasets[0].data = [s1, s2, s3, s4, s5];
                myChart.update();
            }

            autoSaveData();
        }

        function calcInitialTotal() {
            const getNum = (id) => {
                const val = parseInt(getVal(id), 10);
                return isNaN(val) ? 0 : val;
            };

            const r1 = getNum('initR1');
            const r2 = getNum('initR2');
            const r3 = getNum('initR3');
            const r4 = getNum('initR4');
            const r5 = getNum('initR5');

            const sum = r1 + r2 + r3 + r4 + r5;
            const totalEl = document.getElementById('initialTotal');
            if (totalEl) {
                totalEl.innerText = sum;
                if (sum === 100) {
                    totalEl.className = "font-extrabold text-emerald-600 text-base";
                } else {
                    totalEl.className = "font-extrabold text-rose-600 text-base";
                }
            }

            autoSaveData();
        }

        function autoSaveData() {
            const data = {
                studentId: getVal('studentId'),
                studentName: getVal('studentName'),
                myRoleSelect: getVal('myRoleSelect'),
                q2Value: getVal('q2Value'),
                q3Cause: getVal('q3Cause'),
                initR1: getVal('initR1'),
                initR2: getVal('initR2'),
                initR3: getVal('initR3'),
                initR4: getVal('initR4'),
                initR5: getVal('initR5'),
                q5Defense: getVal('q5Defense'),
                officialPosition: getVal('officialPosition'),
                reason1: getVal('reason1'),
                reason2: getVal('reason2'),
                slide1: getVal('slide1'),
                slide2: getVal('slide2'),
                slide3: getVal('slide3'),
                slide4: getVal('slide4'),
                slide5: getVal('slide5'),
                ratioReason: getVal('ratioReason'),
                principle1: getVal('principle1'),
                principle2: getVal('principle2'),
                principle3: getVal('principle3'),
                finalReflection: getVal('finalReflection')
            };
            localStorage.setItem('riat_autonomous_debate', JSON.stringify(data));
        }

        function loadSavedData() {
            const raw = localStorage.getItem('riat_autonomous_debate');
            if (!raw) return;

            try {
                const data = JSON.parse(raw);
                setVal('studentId', data.studentId || '');
                setVal('studentName', data.studentName || '');
                setVal('myRoleSelect', data.myRoleSelect || '');
                setVal('q2Value', data.q2Value || '');
                setVal('q3Cause', data.q3Cause || '');
                setVal('initR1', data.initR1 || 0);
                setVal('initR2', data.initR2 || 0);
                setVal('initR3', data.initR3 || 0);
                setVal('initR4', data.initR4 || 0);
                setVal('initR5', data.initR5 || 0);
                setVal('q5Defense', data.q5Defense || '');
                setVal('officialPosition', data.officialPosition || '');
                setVal('reason1', data.reason1 || '');
                setVal('reason2', data.reason2 || '');
                setVal('slide1', data.slide1 || 20);
                setVal('slide2', data.slide2 || 20);
                setVal('slide3', data.slide3 || 20);
                setVal('slide4', data.slide4 || 20);
                setVal('slide5', data.slide5 || 20);
                setVal('ratioReason', data.ratioReason || '');
                setVal('principle1', data.principle1 || '');
                setVal('principle2', data.principle2 || '');
                setVal('principle3', data.principle3 || '');
                setVal('finalReflection', data.finalReflection || '');

                updateChart();
            } catch (e) {
                console.error("로컬 데이터 로드 오류", e);
            }
        }

        function exportToPDF() {
            showToast('PDF 생성 중입니다...');
            const element = document.querySelector('.max-w-5xl');
            const studentId = getVal('studentId').trim();
            const studentName = getVal('studentName').trim();
            
            let pdfFileName = '자율주행자동차 토론.pdf';
            if (studentId || studentName) {
                pdfFileName = `자율주행자동차 토론(${studentId}_${studentName}).pdf`;
            }

            const opt = {
                margin:       [0.3, 0.3, 0.3, 0.3],
                filename:     pdfFileName,
                image:        { type: 'jpeg', quality: 0.98 },
                html2canvas:  { scale: 2, useCORS: true, ignoreElements: (node) => node.classList && node.classList.contains('no-print') },
                jsPDF:        { unit: 'in', format: 'a4', orientation: 'portrait' }
            };

            if (typeof html2pdf !== 'undefined') {
                html2pdf().set(opt).from(element).save().then(() => showToast('PDF 다운로드 완료!'));
            }
        }

        function showToast(msg) {
            const toast = document.getElementById('toast');
            const toastMsg = document.getElementById('toastMsg');
            if (!toast || !toastMsg) return;
            toastMsg.innerText = msg;
            toast.classList.remove('opacity-0');
            toast.classList.add('opacity-100');
            setTimeout(() => {
                toast.classList.remove('opacity-100');
                toast.classList.add('opacity-0');
            }, 2500);
        }
    </script>
</body>
</html>
