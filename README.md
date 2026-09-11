[main.js](https://github.com/user-attachments/files/32105300/main.js)
⬇[index.html](https://github.com/user-attachments/files/32105310/index.html)<!DOCTYPE html>
<html lang="ur" dir="ltr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Al Behlool Hotel | Online Order</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700;800&family=Noto+Nastaliq+Urdu:wght@400;700&display=swap" rel="stylesheet">

    <style>
        body {
            font-family: 'Poppins', sans-serif;
            background-color: #0f172a;
            color: #f8fafc;
            overflow-x: hidden;
        }

        /* 3D Intro Animations */
        .intro-bg {
            background: radial-gradient(circle at center, #1e293b 0%, #090d16 100%);
        }

        .text-3d {
            font-weight: 900;
            text-transform: uppercase;
            color: #f59e0b;
            text-shadow: 
                0 1px 0 #d97706,
                0 2px 0 #b45309,
                0 3px 0 #92400e,
                0 4px 0 #78350f,
                0 5px 10px rgba(0,0,0,0.8),
                0 0 20px rgba(245, 158, 11, 0.5);
            transform: perspective(500px) rotateX(15deg);
        }

        @keyframes float3d {
            0% { transform: translateY(0px) rotate(0deg) scale(1); }
            50% { transform: translateY(-20px) rotate(5deg) scale(1.05); }
            100% { transform: translateY(0px) rotate(0deg) scale(1); }
        }

        .floating-dish-1 { animation: float3d 4s ease-in-out infinite; }
        .floating-dish-2 { animation: float3d 5s ease-in-out infinite 1s; }
        .floating-dish-3 { animation: float3d 4.5s ease-in-out infinite 0.5s; }

        /* 3D Card Hover Effect */
        .food-card {
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            transform-style: preserve-3d;
        }

        .food-card:hover {
            transform: translateY(-10px) rotateX(5deg) rotateY(-2deg);
            box-shadow: 0 20px 30px -10px rgba(245, 158, 11, 0.3);
        }

        .urdu-text {
            font-family: 'Noto Nastaliq Urdu', serif;
        }
    </style>
</head>
<body>

    <!-- ================= 1. 3D INTRO SCREEN ================= -->
    <div id="intro-screen" class="fixed inset-0 z-50 intro-bg flex flex-col justify-center items-center text-center p-4 transition-opacity duration-1000">
        
        <!-- Floating 3D Dishes Background -->
        <div class="absolute inset-0 pointer-events-none overflow-hidden opacity-30">
            <img src="https://images.unsplash.com/photo-1599488615731-7e5c2823ff28?w=300" class="absolute top-10 left-10 w-32 md:w-48 rounded-full shadow-2xl floating-dish-1 border-2 border-amber-500" alt="Kabab">
            <img src="https://images.unsplash.com/photo-1603894584373-5ac82b2ae398?w=300" class="absolute bottom-12 right-10 w-36 md:w-52 rounded-full shadow-2xl floating-dish-2 border-2 border-amber-500" alt="Karahi">
            <img src="https://images.unsplash.com/photo-1563379091339-03b21ab4a4f8?w=300" class="absolute top-1/3 right-12 w-28 md:w-40 rounded-full shadow-2xl floating-dish-3 border-2 border-amber-500" alt="Biryani">
        </div>

        <!-- 3D Developer Title -->
        <div class="z-10 space-y-4">
            <p class="text-amber-400 tracking-widest uppercase font-bold text-sm md:text-base animate-pulse">Designed & Developed By</p>
            <h1 class="text-4xl md:text-7xl text-3d tracking-wider">WAQAS DEVELOPER</h1>
            <p class="text-slate-300 text-lg md:text-2xl font-semibold mt-2">Presents</p>
            
            <div class="mt-6 p-4 bg-slate-800/80 backdrop-blur-md rounded-2xl border border-amber-500/30 max-w-md mx-auto shadow-2xl">
                <h2 class="text-3xl font-extrabold text-amber-500 urdu-text">البلول ہوٹل</h2>
                <p class="text-xs text-slate-400 mt-1">دیپالپور روڈ نزد مغل سٹیل ورکس، اوکاڑہ</p>
            </div>

            <button onclick="enterWebsite()" class="mt-8 px-8 py-3 bg-gradient-to-r from-amber-500 to-red-600 text-white font-bold rounded-full shadow-lg hover:scale-105 transition transform flex items-center gap-3 mx-auto">
                <span>View Menu & Order</span>
                <i class="fa-solid fa-arrow-right"></i>
            </button>
        </div>
    </div>

    <!-- ================= 2. MAIN KFC STYLE WEBSITE ================= -->
    <div id="main-content" class="min-h-screen flex flex-col">
        
        <!-- Header -->
        <header class="sticky top-0 z-40 bg-slate-900/90 backdrop-blur-md border-b border-slate-800 px-4 lg:px-12 py-3 flex justify-between items-center">
            <div class="flex items-center gap-3">
                <div class="w-10 h-10 bg-amber-500 rounded-full flex items-center justify-center font-black text-slate-900 text-xl shadow-lg">
                    AB
                </div>
                <div>
                    <h1 class="text-xl font-bold text-amber-400 leading-none">Al Behlool Hotel</h1>
                    <span class="text-xs text-slate-400">Okara • 0310-7771277</span>
                </div>
            </div>

            <!-- Search & Cart -->
            <div class="flex items-center gap-4">
                <button onclick="toggleCart()" class="relative bg-amber-500/10 border border-amber-500/30 text-amber-400 px-4 py-2 rounded-full flex items-center gap-2 hover:bg-amber-500 hover:text-slate-900 transition">
                    <i class="fa-solid fa-cart-shopping text-lg"></i>
                    <span class="font-bold hidden sm:inline">Cart</span>
                    <span id="cart-count" class="bg-red-600 text-white text-xs w-5 h-5 rounded-full flex items-center justify-center font-bold">0</span>
                </button>
            </div>
        </header>

        <!-- Banner -->
        <section class="relative bg-gradient-to-r from-red-900 to-slate-900 text-white py-12 px-6 lg:px-12 overflow-hidden">
            <div class="max-w-6xl mx-auto flex flex-col md:flex-row items-center justify-between gap-6 relative z-10">
                <div class="space-y-3 text-center md:text-left">
                    <span class="bg-amber-500/20 text-amber-400 text-xs font-bold px-3 py-1 rounded-full border border-amber-500/30">دیسی مرغ و دیسی گھی میں</span>
                    <h2 class="text-3xl md:text-5xl font-black text-white">Delicious BBQ & Karahi</h2>
                    <p class="text-slate-300 text-sm max-w-md">فریش اور باذائقہ کھانا اب آن لائن آرڈر کریں اور ڈائریکٹ واٹس ایپ پر آرڈر بھیجیں۔</p>
                </div>
                <div class="w-48 h-48 md:w-64 md:h-64 rounded-full overflow-hidden border-4 border-amber-500/50 shadow-2xl">
                    <img src="https://images.unsplash.com/photo-1603894584373-5ac82b2ae398?w=500" class="w-full h-full object-cover" alt="Karahi">
                </div>
            </div>
        </section>

        <!-- Categories Bar -->
        <nav class="sticky top-16 z-30 bg-slate-900/95 border-b border-slate-800 py-3 px-4 overflow-x-auto whitespace-nowrap">
            <div class="flex gap-2 max-w-6xl mx-auto" id="category-buttons">
                <!-- JS will generate category buttons here -->
            </div>
        </nav>

        <!-- Main Items Grid -->
        <main class="flex-grow max-w-6xl w-full mx-auto p-4 md:p-6 my-4">
            <div id="food-grid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
                <!-- JS will populate menu items dynamically -->
            </div>
        </main>

        <!-- Footer -->
        <footer class="bg-slate-950 border-t border-slate-800 text-slate-400 py-6 px-4 text-center text-sm space-y-2">
            <p>© 2026 <strong class="text-amber-400">Al Behlool Hotel</strong>. All Rights Reserved.</p>
            <p class="text-xs text-slate-500">Website Crafted with ❤️ by <span class="text-amber-500 font-bold">Waqas Developer</span></p>
        </footer>
    </div>

    <!-- ================= 3. CART SIDEBAR ================= -->
    <div id="cart-modal" class="fixed inset-0 z-50 bg-black/60 backdrop-blur-sm hidden flex justify-end">
        <div class="bg-slate-900 w-full max-w-md h-full flex flex-col p-6 shadow-2xl border-l border-slate-800">
            <div class="flex justify-between items-center border-b border-slate-800 pb-4">
                <h3 class="text-xl font-bold text-amber-400 flex items-center gap-2">
                    <i class="fa-solid fa-bag-shopping"></i> Your Order
                </h3>
                <button onclick="toggleCart()" class="text-slate-400 hover:text-white text-2xl">&times;</button>
            </div>

            <!-- Cart Items List -->
            <div id="cart-items" class="flex-grow overflow-y-auto py-4 space-y-3">
                <!-- Dynamic Items -->
            </div>

            <!-- Checkout Section -->
            <div class="border-t border-slate-800 pt-4 space-y-4">
                <div class="flex justify-between items-center text-lg font-bold">
                    <span>Total Amount:</span>
                    <span id="cart-total" class="text-amber-400 text-2xl">Rs. 0</span>
                </div>

                <div class="space-y-2">
                    <label class="text-xs text-slate-400">Customer Name & Address:</label>
                    <input type="text" id="cust-name" placeholder="آپ کا نام (Your Name)" class="w-full bg-slate-800 border border-slate-700 rounded-lg p-2.5 text-sm text-white focus:outline-none focus:border-amber-500">
                    <input type="text" id="cust-address" placeholder="ڈیلیوری ایڈریس (Address in Okara)" class="w-full bg-slate-800 border border-slate-700 rounded-lg p-2.5 text-sm text-white focus:outline-none focus:border-amber-500">
                </div>

                <button onclick="sendWhatsAppOrder()" class="w-full py-3 bg-green-600 hover:bg-green-500 text-white font-bold rounded-xl shadow-lg flex items-center justify-center gap-2 transition">
                    <i class="fa-brands fa-whatsapp text-2xl"></i>
                    <span>Order via WhatsApp Now</span>
                </button>
            </div>
        </div>
    </div>

    <!-- ================= SCRIPT & DATA ================= -->
    <script>
        // WhatsApp target number
        const PHONE_NUMBER = "923107771277"; // 03107771277

        // Menu Data extracted from reference image
        const menuItems = [
            // BBQ
            { id: 1, name: "Chicken Kabab (چکن کباب)", category: "bbq", price: 160, img: "https://images.unsplash.com/photo-1599488615731-7e5c2823ff28?w=400" },
            { id: 2, name: "Chicken Tikka Boti (چکن تکہ بوٹی)", category: "bbq", price: 170, img: "https://images.unsplash.com/photo-1555939594-58d7cb561ad1?w=400" },
            { id: 3, name: "Chicken Achari Boti (چکن اچاری بوٹی)", category: "bbq", price: 190, img: "https://images.unsplash.com/photo-1610057099431-d73a1c9d2f2f?w=400" },
            { id: 4, name: "Beef Kabab (بیف کباب)", category: "bbq", price: 200, img: "https://images.unsplash.com/photo-1529193591184-b1d58069ecdd?w=400" },
            { id: 5, name: "Chicken Reshmi Kabab (چکن ریشمی کباب)", category: "bbq", price: 230, img: "https://images.unsplash.com/photo-1599488615731-7e5c2823ff28?w=400" },
            { id: 6, name: "Chicken Cheese Kabab (چکن چیز کباب)", category: "bbq", price: 250, img: "https://images.unsplash.com/photo-1544025162-d76694265947?w=400" },
            { id: 7, name: "Chicken Malai Boti (چکن ملائی بوٹی)", category: "bbq", price: 280, img: "https://images.unsplash.com/photo-1610057099431-d73a1c9d2f2f?w=400" },
            { id: 8, name: "Chicken Leg Piece (چکن لیگ پیس)", category: "bbq", price: 380, img: "https://images.unsplash.com/photo-1598515214211-89d3c73ae83b?w=400" },
            { id: 9, name: "Chicken Chest Piece (چکن چیسٹ پیس)", category: "bbq", price: 400, img: "https://images.unsplash.com/photo-1598515214211-89d3c73ae83b?w=400" },

            // Pakistani Dishes / Karahi
            { id: 10, name: "Special Desi Murgh Karahi (اسپیشل دیسی مرغ کڑاہی)", category: "karahi", price: 3800, img: "https://images.unsplash.com/photo-1603894584373-5ac82b2ae398?w=400" },
            { id: 11, name: "Chicken Golden Karahi (چکن گولڈن کڑاہی)", category: "karahi", price: 2000, img: "https://images.unsplash.com/photo-1603894584373-5ac82b2ae398?w=400" },
            { id: 12, name: "Special White Karahi (اسپیشل چکن وائٹ کڑاہی)", category: "karahi", price: 1900, img: "https://images.unsplash.com/photo-1565557623262-b51c2513a641?w=400" },
            { id: 13, name: "Chicken Karahi Full (چکن کڑاہی فل)", category: "karahi", price: 1750, img: "https://images.unsplash.com/photo-1603894584373-5ac82b2ae398?w=400" },
            { id: 14, name: "Mutton Karahi Full (مٹن کڑاہی فل)", category: "karahi", price: 3800, img: "https://images.unsplash.com/photo-1545247181-516773cae754?w=400" },
            { id: 15, name: "Beef Karahi Full (بیف کڑاہی فل)", category: "karahi", price: 2400, img: "https://images.unsplash.com/photo-1545247181-516773cae754?w=400" },

            // Rice
            { id: 16, name: "Chicken Biryani (چکن بریانی)", category: "rice", price: 250, img: "https://images.unsplash.com/photo-1563379091339-03b21ab4a4f8?w=400" },
            { id: 17, name: "Chicken Fried Rice (چکن فرائیڈ رائس)", category: "rice", price: 600, img: "https://images.unsplash.com/photo-1603133872878-684f208fb84b?w=400" },
            { id: 18, name: "Chicken Masala Rice (چکن مصالحہ رائس)", category: "rice", price: 700, img: "https://images.unsplash.com/photo-1563379091339-03b21ab4a4f8?w=400" },

            // Tandoor
            { id: 19, name: "Roghni Naan (روغنی نان)", category: "tandoor", price: 70, img: "https://images.unsplash.com/photo-1626074353765-517a681e40be?w=400" },
            { id: 20, name: "Garlic Naan (گارلک نان)", category: "tandoor", price: 90, img: "https://images.unsplash.com/photo-1626074353765-517a681e40be?w=400" },
            { id: 21, name: "Cheese Naan (چیز نان)", category: "tandoor", price: 250, img: "https://images.unsplash.com/photo-1565557623262-b51c2513a641?w=400" },
            { id: 22, name: "Sada Roti (سادہ روٹی)", category: "tandoor", price: 20, img: "https://images.unsplash.com/photo-1626074353765-517a681e40be?w=400" },

            // Drinks
            { id: 23, name: "1.5 Liter Cold Drink", category: "drinks", price: 200, img: "https://images.unsplash.com/photo-1622483767028-3f66f32aef97?w=400" },
            { id: 24, name: "1 Liter Cold Drink", category: "drinks", price: 160, img: "https://images.unsplash.com/photo-1622483767028-3f66f32aef97?w=400" },
            { id: 25, name: "Special Doodh Patti (دودھ پتی)", category: "drinks", price: 100, img: "https://images.unsplash.com/photo-1576092768241-dec231879fc3?w=400" }
        ];

        const categories = [
            { id: "all", name: "All Items (تمام ڈشز)" },
            { id: "bbq", name: "Barbeque (باربی کیو)" },
            { id: "karahi", name: "Karahi & Handi (کڑاہی)" },
            { id: "rice", name: "Rice (رائس)" },
            { id: "tandoor", name: "Tandoor (تندور)" },
            { id: "drinks", name: "Beverages (کولڈ ڈرنکس)" }
        ];

        let cart = [];

        // Intro Screen Dismiss
        function enterWebsite() {
            const intro = document.getElementById('intro-screen');
            intro.classList.add('opacity-0');
            setTimeout(() => {
                intro.style.display = 'none';
            }, 1000);
        }

        // Render Categories
        function renderCategories() {
            const container = document.getElementById('category-buttons');
            container.innerHTML = categories.map(cat => `
                <button onclick="filterCategory('${cat.id}')" id="cat-${cat.id}" class="px-5 py-2 rounded-full font-semibold text-sm border border-slate-700 hover:border-amber-500 hover:text-amber-400 transition ${cat.id === 'all' ? 'bg-amber-500 text-slate-900 border-amber-500 font-bold' : 'bg-slate-800 text-slate-300'}">
                    ${cat.name}
                </button>
            `).join('');
        }

        // Render Food Items
        function renderItems(filter = 'all') {
            const grid = document.getElementById('food-grid');
            const filtered = filter === 'all' ? menuItems : menuItems.filter(i => i.category === filter);

            grid.innerHTML = filtered.map(item => `
                <div class="food-card bg-slate-800/80 rounded-2xl overflow-hidden border border-slate-700/60 shadow-xl flex flex-col justify-between">
                    <div>
                        <div class="relative h-44 overflow-hidden">
                            <img src="${item.img}" class="w-full h-full object-cover transform hover:scale-110 transition duration-500" alt="${item.name}">
                            <span class="absolute top-3 right-3 bg-slate-900/80 backdrop-blur-md text-amber-400 font-extrabold px-3 py-1 rounded-full text-sm border border-amber-500/30">
                                Rs. ${item.price}
                            </span>
                        </div>
                        <div class="p-4">
                            <h3 class="font-bold text-lg text-white leading-snug">${item.name}</h3>
                            <p class="text-xs text-slate-400 mt-1">Al Behlool Hotel Special Quality Item</p>
                        </div>
                    </div>
                    <div class="p-4 pt-0 flex gap-2">
                        <button onclick="addToCart(${item.id})" class="flex-1 py-2.5 bg-gradient-to-r from-amber-500 to-amber-600 hover:from-amber-600 hover:to-amber-700 text-slate-950 font-bold rounded-xl text-sm transition shadow-md flex items-center justify-center gap-2">
                            <i class="fa-solid fa-plus"></i> Add to Cart
                        </button>
                        <button onclick="directOrder(${item.id})" class="px-3 py-2.5 bg-green-600/20 text-green-400 hover:bg-green-600 hover:text-white border border-green-500/30 font-bold rounded-xl text-xs transition" title="Quick WhatsApp Order">
                            <i class="fa-brands fa-whatsapp text-lg"></i>
                        </button>
                    </div>
                </div>
            `).join('');
        }

        // Filter Action
        function filterCategory(catId) {
            categories.forEach(c => {
                const btn = document.getElementById(`cat-${c.id}`);
                if (btn) {
                    if (c.id === catId) {
                        btn.className = "px-5 py-2 rounded-full font-bold text-sm bg-amber-500 text-slate-900 border border-amber-500 transition";
                    } else {
                        btn.className = "px-5 py-2 rounded-full font-semibold text-sm bg-slate-800 text-slate-300 border border-slate-700 hover:border-amber-500 hover:text-amber-400 transition";
                    }
                }
            });
            renderItems(catId);
        }

        // Cart Actions
        function addToCart(id) {
            const item = menuItems.find(i => i.id === id);
            const exist = cart.find(i => i.id === id);
            if (exist) {
                exist.qty += 1;
            } else {
                cart.push({ ...item, qty: 1 });
            }
            updateCartUI();
        }

        function updateCartUI() {
            const count = cart.reduce((sum, item) => sum + item.qty, 0);
            const total = cart.reduce((sum, item) => sum + (item.price * item.qty), 0);
            
            document.getElementById('cart-count').innerText = count;
            document.getElementById('cart-total').innerText = `Rs. ${total}`;

            const cartContainer = document.getElementById('cart-items');
            if (cart.length === 0) {
                cartContainer.innerHTML = `<div class="text-center text-slate-500 py-12"><i class="fa-solid fa-basket-shopping text-4xl mb-2"></i><p>Your Cart is empty</p></div>`;
            } else {
                cartContainer.innerHTML = cart.map(item => `
                    <div class="flex justify-between items-center bg-slate-800 p-3 rounded-xl border border-slate-700">
                        <div>
                            <p class="font-bold text-sm text-white">${item.name}</p>
                            <p class="text-xs text-amber-400">Rs. ${item.price} x ${item.qty} = Rs. ${item.price * item.qty}</p>
                        </div>
                        <div class="flex items-center gap-2">
                            <button onclick="changeQty(${item.id}, -1)" class="w-7 h-7 bg-slate-700 text-white rounded-lg text-sm font-bold hover:bg-slate-600">-</button>
                            <span class="font-bold text-sm">${item.qty}</span>
                            <button onclick="changeQty(${item.id}, 1)" class="w-7 h-7 bg-amber-500 text-slate-900 rounded-lg text-sm font-bold hover:bg-amber-400">+</button>
                        </div>
                    </div>
                `).join('');
            }
        }

        function changeQty(id, delta) {
            const item = cart.find(i => i.id === id);
            if (item) {
                item.qty += delta;
                if (item.qty <= 0) {
                    cart = cart.filter(i => i.id !== id);
                }
            }
            updateCartUI();
        }

        function toggleCart() {
            const modal = document.getElementById('cart-modal');
            modal.classList.toggle('hidden');
        }

        // WhatsApp Checkout Logic
        function sendWhatsAppOrder() {
            if (cart.length === 0) {
                alert("براہ کرم پہلے مینو سے کوئی ڈش منتخب کریں۔ (Please select an item first)");
                return;
            }

            const name = document.getElementById('cust-name').value || "Customer";
            const address = document.getElementById('cust-address').value || "Okara";

            let message = `*NEW ORDER - AL BEHLOOL HOTEL*\n`;
            message += `-----------------------------\n`;
            message += `👤 *Name:* ${name}\n`;
            message += `📍 *Address:* ${address}\n\n`;
            message += `*ORDER ITEMS:*\n`;

            let total = 0;
            cart.forEach((item, index) => {
                const itemTotal = item.price * item.qty;
                total += itemTotal;
                message += `${index + 1}. ${item.name} x ${item.qty} = Rs. ${itemTotal}\n`;
            });

            message += `-----------------------------\n`;
            message += `💰 *Total Bill:* Rs. ${total}\n`;
            message += `-----------------------------\n`;
            message += `*Website Developed by Waqas Developer*`;

            const encodedMsg = encodeURIComponent(message);
            window.open(`https://wa.me/${PHONE_NUMBER}?text=${encodedMsg}`, '_blank');
        }

        // Direct Quick Order via WhatsApp for single item
        function directOrder(id) {
            const item = menuItems.find(i => i.id === id);
            let message = `*QUICK ORDER - AL BEHLOOL HOTEL*\n`;
            message += `-----------------------------\n`;
            message += `🍽️ *Item:* ${item.name}\n`;
            message += `💰 *Price:* Rs. ${item.price}\n`;
            message += `-----------------------------\n`;
            message += `براہ کرم میرا آرڈر کنفرم کریں۔\n`;
            message += `*Website Developed by Waqas Developer*`;

            const encodedMsg = encodeURIComponent(message);
            window.open(`https://wa.me/${PHONE_NUMBER}?text=${encodedMsg}`, '_blank');
        }

        // Initial Load
        renderCategories();
        renderItems();
    </script>
</body>
</html>
