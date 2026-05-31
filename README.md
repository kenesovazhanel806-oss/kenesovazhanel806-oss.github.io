<!DOCTYPE html><html lang="kk"><head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TravelTour - Әуе билеттері мен Ыстық турлар</title>
    <style>
        /* Жалпы баптаулар */
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Segoe UI', Arial, sans-serif; scroll-behavior: smooth; }
        body { background-color: #f0f4f8; color: #333; }

        /* БАСТЫ БЕТ (ҰШАҚ СУРЕТІ МЕН АҚ-КӨК СТИЛЬ) */
        .welcome-section {
            height: 100vh;
            background: linear-gradient(rgba(15, 32, 67, 0.85), rgba(27, 55, 107, 0.85)), 
                        url('https://images.unsplash.com/photo-1436491865332-7a61a109cc05?auto=format&fit=crop&w=1920&q=80') no-repeat center center/cover;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            color: white;
            text-align: center;
            padding: 20px;
        }

        .welcome-section h1 { font-size: 4rem; font-weight: 800; margin-bottom: 15px; letter-spacing: 3px; text-shadow: 0 4px 10px rgba(0,0,0,0.3); }
        .welcome-section p { font-size: 1.6rem; margin-bottom: 40px; opacity: 0.95; max-width: 650px; font-weight: 300; }

        /* БАТЫРМАЛАР СТИЛІ МЕН АНИМАЦИЯСЫ */
        .buttons-container { display: flex; gap: 25px; flex-wrap: wrap; justify-content: center; }
        
        .nav-btn {
            display: inline-block;
            background: white;
            color: #1b376b;
            padding: 18px 45px;
            font-size: 1.3rem;
            font-weight: bold;
            text-decoration: none;
            border-radius: 50px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.2);
            transition: all 0.2s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            border: 2px solid white;
            cursor: pointer;
            user-select: none;
        }

        .nav-btn:hover {
            background: transparent;
            color: white;
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(255,255,255,0.2);
        }

        .nav-btn:active {
            transform: translateY(2px) scale(0.95);
            box-shadow: 0 5px 10px rgba(0,0,0,0.2);
        }

        /* НЕГІЗГІ БӨЛІМДЕР */
        .container { max-width: 1200px; margin: 0 auto; padding: 70px 20px; }
        h2 { text-align: center; margin-bottom: 45px; color: #1b376b; font-size: 2.2rem; font-weight: 700; text-transform: uppercase; letter-spacing: 1px; position: relative; }
        h2::after { content: ''; display: block; width: 60px; height: 4px; background: #2a5298; margin: 10px auto 0; border-radius: 2px; }
        
        /* Карточкалар торы */
        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 30px; margin-bottom: 60px; }
        .card { background: white; border-radius: 20px; overflow: hidden; box-shadow: 0 10px 20px rgba(0,0,0,0.05); transition: all 0.3s ease; border: 1px solid rgba(0,0,0,0.03); }
        .card:hover { transform: translateY(-8px); box-shadow: 0 15px 30px rgba(0,0,0,0.12); }
        .card-img { height: 200px; background-size: cover; background-position: center; position: relative; }
        
        /* Суреттер */
        .img-dubai { background-image: url('https://images.unsplash.com/photo-1512453979798-5ea266f8880c?auto=format&fit=crop&w=500&q=80'); }
        .img-antalya { background-image: url('https://images.unsplash.com/photo-1542314831-068cd1dbfeeb?auto=format&fit=crop&w=500&q=80'); }
        .img-almaty { background-image: url('https://images.unsplash.com/photo-1589561253898-768105ca91a8?auto=format&fit=crop&w=500&q=80'); }
        .img-aktobe { background-image: url('https://images.unsplash.com/photo-1569154941061-e231b4725ef1?auto=format&fit=crop&w=500&q=80'); }
        .img-tashkent { background-image: url('https://images.unsplash.com/photo-1528127269322-539801943592?auto=format&fit=crop&w=500&q=80'); }
        .img-shymkent { background-image: url('https://images.unsplash.com/photo-1533105079780-92b9be482077?auto=format&fit=crop&w=500&q=80'); }

        .card-body { padding: 25px; display: flex; flex-direction: column; justify-content: space-between; }
        .card-title { font-size: 1.3rem; margin-bottom: 10px; color: #2c3e50; font-weight: 700; }
        .card-text { color: #7f8c8d; font-size: 0.95rem; margin-bottom: 20px; line-height: 1.6; }
        .price { font-size: 1.4rem; font-weight: bold; color: #2a5298; margin-bottom: 20px; background: #eef3f9; padding: 8px 15px; border-radius: 10px; display: inline-block; width: max-content; }
        
        /* КАРТОЧКА ІШІНДЕГІ БАТЫРМАЛАР */
        .btn-buy { 
            display: block; 
            text-align: center; 
            background: linear-gradient(135deg, #25d366, #1ebd54);
            color: white; 
            text-decoration: none; 
            padding: 14px; 
            border-radius: 12px; 
            font-weight: bold; 
            font-size: 1.1rem; 
            transition: all 0.2s ease; 
            cursor: pointer; 
            border: none; 
            width: 100%;
            user-select: none;
            box-shadow: 0 5px 15px rgba(37, 211, 102, 0.3);
        }
        .btn-buy:hover { background: linear-gradient(135deg, #20ba5a, #1a9f47); transform: translateY(-2px); box-shadow: 0 8px 20px rgba(37, 211, 102, 0.4); }
        
        .btn-blue { background: linear-gradient(135deg, #2a5298, #1e3c72); box-shadow: 0 5px 15px rgba(42, 82, 152, 0.3); }
        .btn-blue:hover { background: linear-gradient(135deg, #1e3c72, #152b52); box-shadow: 0 8px 20px rgba(42, 82, 152, 0.4); }
        
        .btn-orange { background: linear-gradient(135deg, #ff9800, #f57c00); color: white; box-shadow: 0 5px 15px rgba(255, 152, 0, 0.3); }
        .btn-orange:hover { background: linear-gradient(135deg, #e68a00, #d86d00); box-shadow: 0 8px 20px rgba(255, 152, 0, 0.4); }

        /* 🆕 О НАС (БІЗ ТУРАЛЫ) БӨЛІМІНІҢ ДИЗАЙНЫ */
        .about-section { background: linear-gradient(135deg, #1b376b, #0f2043); color: white; padding: 80px 20px; text-align: center; }
        .about-section h2 { color: white; }
        .about-section h2::after { background: #ff9800; }
        .about-container { max-width: 1000px; margin: 0 auto; display: flex; flex-direction: column; gap: 30px; align-items: center; margin-top: 40px; }
        .about-text { font-size: 1.2rem; line-height: 1.8; opacity: 0.9; max-width: 800px; font-weight: 300; }
        
        /* Аэропорт концепттерінің торы */
        .airport-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 20px; width: 100%; margin-top: 30px; }
        .airport-badge { background: rgba(255, 255, 255, 0.08); padding: 20px; border-radius: 15px; border: 1px solid rgba(255, 255, 255, 0.1); text-align: left; transition: 0.3s; }
        .airport-badge:hover { background: rgba(255, 255, 255, 0.15); transform: translateY(-5px); }
        .airport-badge h4 { color: #ff9800; font-size: 1.2rem; margin-bottom: 8px; }
        .airport-badge p { font-size: 0.9rem; opacity: 0.8; line-height: 1.4; }

        /* Модальное окно */
        .modal {
            display: none;
            position: fixed;
            z-index: 1000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(15, 32, 67, 0.6);
            justify-content: center;
            align-items: center;
            backdrop-filter: blur(5px);
        }

        .modal-content {
            background-color: rgba(255, 255, 255, 0.95);
            padding: 35px;
            border-radius: 24px;
            width: 90%;
            max-width: 460px;
            box-shadow: 0 20px 50px rgba(0,0,0,0.3);
            position: relative;
            animation: bounceIn 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
        }

        .hawaii-bg {
            background: linear-gradient(rgba(255, 255, 255, 0.88), rgba(255, 255, 255, 0.88)), 
                        url('https://images.unsplash.com/photo-1507525428034-b723cf961d3e?auto=format&fit=crop&w=500&q=80') no-repeat center center/cover;
        }

        @keyframes bounceIn {
            from { transform: translateY(-80px) scale(0.9); opacity: 0; }
            to { transform: translateY(0) scale(1); opacity: 1; }
        }

        .close-btn { position: absolute; top: 18px; right: 22px; font-size: 1.8rem; cursor: pointer; color: #999; transition: 0.2s; }
        .close-btn:hover { color: #333; transform: rotate(90deg); }

        .modal h3 { margin-bottom: 25px; color: #1b376b; text-align: center; font-size: 1.6rem; font-weight: 700; }
        .modal p { font-size: 1.1rem; text-align: center; margin-bottom: 25px; color: #4a5568; line-height: 1.6; }
        
        .form-group { margin-bottom: 18px; }
        .form-group label { display: block; margin-bottom: 8px; font-weight: 600; font-size: 0.95rem; color: #4a5568; }
        .form-group input, .form-group select {
            width: 100%;
            padding: 14px;
            border: 1px solid #cbd5e1;
            border-radius: 12px;
            font-size: 1rem;
            outline: none;
            background: white;
            transition: all 0.2s;
            color: #334155;
        }
        .form-group input:focus, .form-group select:focus { border-color: #2a5298; box-shadow: 0 0 0 4px rgba(42, 82, 152, 0.15); }

        .price-display {
            background: linear-gradient(135deg, #fff8e1, #ffecb3);
            border: 1px solid #ffe082;
            padding: 12px;
            border-radius: 12px;
            text-align: center;
            font-size: 1.3rem;
            font-weight: bold;
            color: #b78103;
            margin-bottom: 20px;
            animation: pulse 1.5s infinite;
        }

        @keyframes pulse { 0% { transform: scale(1); } 50% { transform: scale(1.02); } 100% { transform: scale(1); } }

        .whatsapp-number-box { background-color: #f0fdf4; border: 2px dashed #25d366; padding: 15px; border-radius: 14px; text-align: center; font-size: 1.3rem; font-weight: bold; color: #166534; margin-bottom: 20px; }
        footer { background: #0f2043; color: white; text-align: center; padding: 30px; font-size: 1rem; font-weight: 300; border-top: 1px solid rgba(255,255,255,0.05); }
    </style></head><body>

    <!-- БАСТЫ БЕТ -->
    <div class="welcome-section">
        <h1>TRAVEL TOUR</h1>
        <p>Ыңғайлы бағыттар, арзан әуе билеттері мен ең ыстық турлар жиынтығы!</p>
        
        <div class="buttons-container">
            <div onclick="openTourModal('Дубай')" class="nav-btn">✈️ Тур Сатып Алу</div>
            <div onclick="openTicketModal('Алматы - Астана')" class="nav-btn">🎫 Әуе Билеттері</div>
        </div>
    </div>

    <!-- ТУРЛАР БӨЛІМІ -->
    <div class="container" id="tours">
        <h2>Ыстық Турлар жиынтығы</h2>
        <div class="grid">
            <div class="card">
                <div class="card-img img-dubai"></div>
                <div class="card-body">
                    <div class="card-title">Дубай, БАӘ (Ыстық тур)</div>
                    <p class="card-text">5★ қонақ үй, таңғы ас, трансфер және сақтандыру бағаның ішінде. 3 немесе 5 күндік демалыс!</p>
                    <div class="price">150 000 ₸ бастап</div>
                    <button onclick="openTourModal('Дубай')" class="btn-buy">Турға тапсырыс беру</button>
                </div>
            </div>

            <div class="card">
                <div class="card-img img-antalya"></div>
                <div class="card-body">
                    <div class="card-title">Анталия, Түркия (Ыстық тур)</div>
                    <p class="card-text">"All Inclusive" (Бәрі қосылған) жүйесі. Тікелей рейс, жағажайға жақын люкс қонақ үй.</p>
                    <div class="price">130 000 ₸ бастап</div>
                    <button onclick="openTourModal('Түркия')" class="btn-buy">Турға тапсырыс беру</button>
                </div>
            </div>
        </div>
    </div>

    <!-- ӘУЕ БИЛЕТТЕРІ БӨЛІМІ -->
    <div class="container" id="tickets" style="background-color: #fff; border-radius: 24px; box-shadow: 0 15px 40px rgba(0,0,0,0.03);">
        <h2>Танымал әуе билеттері</h2>
        <div class="grid">
            <div class="card">
                <div class="card-img img-almaty"></div>
                <div class="card-body">
                    <div class="card-title">Алматы ⇄ Астана</div>
                    <p class="card-text">Екі жаққа бірдей тиімді баға. Багаж қосылған. Күнделікті ыңғайлы рейстер.</p>
                    <div class="price">35 000 ₸ бастап</div>
                    <button onclick="openTicketModal('Алматы - Астана')" class="btn-buy btn-blue">Билет брондау</button>
                </div>
            </div>

            <div class="card">
                <div class="card-img img-aktobe"></div>
                <div class="card-body">
                    <div class="card-title">Алматы ⇄ Ақтөбе</div>
                    <p class="card-text">Батыс бағыты бойынша ең төменгі тарифтер. Сенімді әрі жылдам ұшу.</p>
                    <div class="price">42 000 ₸ бастап</div>
                    <button onclick="openTicketModal('Алматы - Ақтөбе')" class="btn-buy btn-blue">Билет брондау</button>
                </div>
            </div>

            <div class="card">
                <div class="card-img img-tashkent"></div>
                <div class="card-body">
                    <div class="card-title">Алматы ⇄ Ташкент</div>
                    <p class="card-text">Халықаралық танымал рейс. Көршілес Өзбекстан еліне ең арзан билеттер.</p>
                    <div class="price">55 000 ₸ бастап</div>
                    <button onclick="openTicketModal('Алматы - Ташкент')" class="btn-buy btn-blue">Билет брондау</button>
                </div>
            </div>

            <div class="card">
                <div class="card-img img-shymkent"></div>
                <div class="card-body">
                    <div class="card-title">Астана ⇄ Шымкент</div>
                    <p class="card-text">Оңтүстік астанаға тікелей рейстер. Ыңғайлы уақыттар мен жеңілдіктер.</p>
                    <div class="price">28 000 ₸ бастап</div>
                    <button onclick="openTicketModal('Астана - Шымкент')" class="btn-buy btn-blue">Билет брондау</button>
                </div>
            </div>
        </div>
    </div>

    <!-- 🆕 О НАС / БІЗ ТУРАЛЫ БӨЛІМІ (ФУТУРИСТІК АЭРОПОРТТАР КОНЦЕПТІ) -->
    <div class="about-section" id="about">
        <div class="container" style="padding: 0;">
            <h2>О нас / Біз туралы</h2>
            <div class="about-container">
                <p class="about-text">
                    <b>TravelTour</b> — тек туристік агенттік қана емес, бұл авиация мен болашақ технологияларының тоғысқан жері. 
                    Біз өз клиенттерімізге ең тиімді саяхаттарды ұсынып қана қоймай, заманауи архитектура мен 3D модельдеу арқылы 
                    болашақтың виртуалды әуежай терминалдарын, смарт тіркелу дүңгіршектері (kiosks) мен инновациялық инфрақұрылымдарын жобалаймыз. 
                    Біздің мақсатымыз — ұшу процесін барынша жайлы әрі футуристік ету!
                </p>
                
                <div class="airport-grid">
                    <div class="airport-badge">
                        <h4>✈️ NextGen Terminal</h4>
                        <p>Өзін-өзі жарықтандыратын материалдардан жасалған, заманауи күту залдары бар ультра-люкс 3D әуежай концепті.</p>
                    </div>
                    <div class="airport-badge">
                        <h4>🤖 Smart Kiosks</h4>
                        <p>Пассажирлерді 3 секунд ішінде тіркеуден өткізетін интеллектуалды цифрлық терминалдар жүйесі.</p>
                    </div>
                    <div class="airport-badge">
                        <h4>🌍 Eco-Hub Almaty</h4>
                        <p>Орталық Азиядағы жасыл технологиялармен жабдықталған ең ірі транзиттік әуежай жобасы.</p>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- 🏖️ 1. ТУРЛАРҒА АРНАЛҒАН ОКОШКА -->
    <div id="tourModal" class="modal">
        <div class="modal-content hawaii-bg" id="tourModalContent"></div>
    </div>

    <!-- 🎫 2. ӘУЕ БИЛЕТТЕРІНЕ АРНАЛҒАН ОКОШКА -->
    <div id="ticketModal" class="modal">
        <div class="modal-content" id="ticketModalContent"></div>
    </div>

    <footer>
        <p>&copy; 2026 TravelTour Агенттігі мен Авиация Концепт-Лабораториясы. Барлық құқықтар қорғалған.</p>
    </footer>

    <script>
        var tourModal = document.getElementById("tourModal");
        var ticketModal = document.getElementById("ticketModal");
        var today = new Date().toISOString().split('T')[0];

        // Базалық бағалар
        var tourPrices = {
            "Дубай": { "3": "150 000 ₸", "5": "210 000 ₸" },
            "Түркия": { "3": "130 000 ₸", "5": "185 000 ₸" }
        };

        var baseTicketPrices = {
            "Алматы - Астана": 35000,
            "Алматы - Ақтөбе": 42000,
            "Алматы - Ташкент": 55000,
            "Астана - Шымкент": 28000
        };

        // Уақытқа байланысты баға коэффиценті
        var timeModifiers = {
            "Таңертеңгі рейс (08:30)": 3000,   // Сұраныс жоғары, +3000 ₸
            "Күндізгі рейс (14:15)": 0,       // Базалық баға
            "Kешкі рейс (21:00)": 5000,       // Ең ыңғайлы уақыт, +5000 ₸
            "Түнгі рейс (02:45)": -4000       // Түнгі рейс арзанырақ, -4000 ₸
        };

        function updateTourPriceDisplay() {
            var country = document.getElementById("tourCountrySelect").value;
            var days = document.getElementById("tourDaysSelect").value;
            var price = (tourPrices[country] && tourPrices[country][days]) || "Келісімді";
            document.getElementById("tourPriceVal").innerText = price;
        }

        // ⏱️ УАҚЫТ ПЕН БАҒАНЫ ЕСЕПТЕУ ФУНКЦИЯСЫ
        function updateTicketPriceDisplay() {
            var selectedRoute = document.getElementById("routeSelect").value;
            var selectedTime = document.getElementById("timeSelect").value;
            
            var basePrice = baseTicketPrices[selectedRoute] || 35000;
            var modifier = timeModifiers[selectedTime] || 0;
            
            var finalPrice = basePrice + modifier;
            
            // Форматтап шығару (мысалы, 38000 -> "38 000 ₸")
            document.getElementById("ticketPriceVal").innerText = finalPrice.toLocaleString('ru-RU') + " ₸";
        }

        // --- ТУР ОКОШКАСЫ ---
        function openTourModal(defaultCountry) {
            tourModal.style.display = "flex";
            if(defaultCountry !== "Дубай" && defaultCountry !== "Түркия") { defaultCountry = "Дубай"; }

            document.getElementById("tourModalContent").innerHTML = `
                <span class="close-btn" onclick="closeTourModal()">&times;</span>
                <h3>🏖️ Ыстық турды таңдау</h3>
                <div class="form-group">
                    <label>Қай елге барғыңыз келеді:</label>
                    <select id="tourCountrySelect" onchange="updateTourPriceDisplay()">
                        <option value="Дубай" ${defaultCountry==='Дубай'?'selected':''}>Дубай (БАӘ)</option>
                        <option value="Түркия" ${defaultCountry==='Түркия'?'selected':''}>Түркия (Анталия)</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Демалыс ұзақтығы:</label>
                    <select id="tourDaysSelect" onchange="updateTourPriceDisplay()">
                        <option value="3">3 күн / 2 түн</option>
                        <option value="5">5 күн / 4 түн</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Ұшу күні:</label>
                    <input type="date" id="tourDateInput" min="${today}" value="${today}">
                </div>
                <div class="price-display">Жалпы бағасы: <span id="tourPriceVal">150 000 ₸</span></div>
                <button onclick="nextTourStep()" class="btn-buy">Жалғастыру</button>
            `;
            updateTourPriceDisplay();
        }

        function nextTourStep() {
            var country = document.getElementById("tourCountrySelect").value;
            var days = document.getElementById("tourDaysSelect").value;
            var date = document.getElementById("tourDateInput").value;
            var price = document.getElementById("tourPriceVal").innerText;
            if(!country || !days || !date) { alert("Өрістерді толтырыңыз!"); return; }
            
            document.getElementById("tourModalContent").innerHTML = `
                <span class="close-btn" onclick="closeTourModal()">&times;</span>
                <h3>🏖️ Тапсырысты рәсімдеу</h3>
                <p><b>Бағыт:</b> ${country} туры<br><b>Ұзақтығы:</b> ${days} күн<br><b>Күні:</b> ${date}<br><b>Бағасы:</b> ${price}</p>
                <br><button onclick="confirmTourPurchase('${encodeURIComponent(country)}', '${encodeURIComponent(days)}', '${encodeURIComponent(date)}', '${encodeURIComponent(price)}')" class="btn-buy btn-orange">Рәсімдеу</button>
            `;
        }

        function confirmTourPurchase(country, days, date, price) {
            document.getElementById("tourModalContent").innerHTML = `
                <span class="close-btn" onclick="closeTourModal()">&times;</span>
                <h3>⚠️ Тапсырысты растау</h3>
                <p>Менеджермен байланысу үшін өтіңіз:</p>
                <div class="whatsapp-number-box">📞 +7 (776) 732-88-65</div>
                <button onclick="finalSendTour('${country}', '${days}', '${date}', '${price}')" class="btn-buy">WhatsApp-қа өту</button>
            `;
        }

        function finalSendTour(country, days, date, price) {
            var whatsappUrl = "https://wa.me/77767328865?text=Сәлеметсіз бе! Маған " + country + " еліне " + days + " күндік ыстық тур керек. Күні: " + date + ". Бағасы: " + price;
            window.open(whatsappUrl, '_blank');
            closeTourModal();
        }

        function closeTourModal() { tourModal.style.display = "none"; }

        // --- ӘУЕ БИЛЕТІ ОКОШКАСЫ (УАҚЫТҚА БАЙЛАНЫСТЫ БАҒА ӨЗГЕРЕДІ) ---
        function openTicketModal(defaultRoute) {
            ticketModal.style.display = "flex";
            
            document.getElementById("ticketModalContent").innerHTML = `
                <span class="close-btn" onclick="closeTicketModal()">&times;</span>
                <h3>🎫 Әуе билетін таңдау</h3>
                
                <div class="form-group">
                    <label>Қай бағытқа ұшады:</label>
                    <select id="routeSelect" onchange="updateTicketPriceDisplay()">
                        <option value="Алматы - Астана" ${defaultRoute==='Алматы - Астана'?'selected':''}>Алматы ⇄ Астана</option>
                        <option value="Алматы - Ақтөбе" ${defaultRoute==='Алматы - Ақтөбе'?'selected':''}>Алматы ⇄ Ақтөбе</option>
                        <option value="Алматы - Ташкент" ${defaultRoute==='Алматы - Ташкент'?'selected':''}>Алматы ⇄ Ташкент</option>
                        <option value="Астана - Шымкент" ${defaultRoute==='Астана - Шымкент'?'selected':''}>Астана ⇄ Шымкент</option>
                    </select>
                </div>

                <div class="form-group">
                    <label>Ұшу күні:</label>
                    <input type="date" id="dateInput" min="${today}" value="${today}">
                </div>

                <div class="form-group">
                    <label>Рейс уақыты (Уақытына қарай баға өзгереді):</label>
                    <select id="timeSelect" onchange="updateTicketPriceDisplay()">
                        <option value="Күндізгі рейс (14:15)">Күндізгі рейс (14:15) [Стандарт]</option>
                        <option value="Таңертеңгі рейс (08:30)">Таңертеңгі рейс (08:30) [+3 000 ₸]</option>
                        <option value="Кешкі рейс (21:00)">Кешкі рейс (21:00) [+5 000 ₸]</option>
                        <option value="Түнгі рейс (02:45)">Түнгі рейс (02:45) [-4 000 ₸]</option>
                    </select>
                </div>

                <div class="price-display">
                    Билет бағасы: <span id="ticketPriceVal">35 000 ₸</span>
                </div>

                <button onclick="nextTicketStep()" class="btn-buy btn-blue">Жалғастыру</button>
            `;
            updateTicketPriceDisplay();
        }

        function nextTicketStep() {
            var route = document.getElementById("routeSelect").value;
            var date = document.getElementById("dateInput").value;
            var time = document.getElementById("timeSelect").value;
            var price = document.getElementById("ticketPriceVal").innerText;
            if(!route || !date || !time) { alert("Өрістерді толтырыңыз!"); return; }
            
            document.getElementById("ticketModalContent").innerHTML = `
                <span class="close-btn" onclick="closeTicketModal()">&times;</span>
                <h3>🎫 Тапсырысты рәсімдеу</h3>
                <p><b>Бағыты:</b> ${route}<br><b>Ұшу күні:</b> ${date}<br><b>Уақыты:</b> ${time}<br><b>Бағасы:</b> ${price}</p>
                <br><button onclick="confirmTicketPurchase('${encodeURIComponent(route)}', '${encodeURIComponent(date)}', '${encodeURIComponent(time)}', '${encodeURIComponent(price)}')" class="btn-buy btn-orange">Рәсімдеу</button>
            `;
        }

        function confirmTicketPurchase(route, date, time, price) {
            document.getElementById("ticketModalContent").innerHTML = `
                <span class="close-btn" onclick="closeTicketModal()">&times;</span>
                <h3>⚠️ Тапсырысты растау</h3>
                <p>Билетті сатып алуды нақты растау үшін өтіңіз:</p>
                <div class="whatsapp-number-box">📞 +7 (776) 732-88-65</div>
                <button onclick="finalSendTicket('${route}', '${date}', '${time}', '${price}')" class="btn-buy">WhatsApp-қа өту</button>
            `;
        }

        function finalSendTicket(route, date, time, price) {
            var whatsappUrl = "https://wa.me/77767328865?text=Сәлеметсіз бе! Маған " + route + " бағытына, " + date + " күніне (" + time + ") әуе билеті керек. Бағасы: " + price;
            window.open(whatsappUrl, '_blank');
            closeTicketModal();
        }

        function closeTicketModal() { ticketModal.style.display = "none"; }

        window.onclick = function(event) {
            if (event.target == tourModal) { closeTourModal(); }
            if (event.target == ticketModal) { closeTicketModal(); }
        }
    </script></body></html>
