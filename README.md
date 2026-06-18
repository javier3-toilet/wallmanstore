<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wallman Store</title>
    <style>
        /* Variables de diseño de Wallman Store */
        :root {
            --azul-fondo: #e0f2fe;
            --azul-relampago: #0051ff;
            --blanco: #ffffff;
            --texto-oscuro: #1e293b;
            --gris-claro: #f1f5f9;
            --amarillo-estrella: #f59e0b;
            --verde-whatsapp: #25d366;
            --color-oro: #d4af37;
        }

        /* Estilos generales y tipografías */
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--azul-fondo);
            color: var(--texto-oscuro);
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            overflow-x: hidden; 
            min-height: 100vh;
        }

        header {
            background-color: var(--azul-relampago);
            color: var(--blanco);
            width: 100%;
            padding: 20px 0;
            box-shadow: 0 4px 15px rgba(0, 81, 255, 0.6); 
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
            width: 100%;
            box-sizing: border-box;
        }

        .header-logo-container {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .header-logo-svg {
            width: 40px;
            height: 32px;
        }

        h1 {
            margin: 0;
            font-size: 2.2rem; 
            font-weight: 900; 
            text-transform: uppercase;
            letter-spacing: 3px; 
            text-shadow: 0 0 10px rgba(255, 255, 255, 0.6), 0 0 20px rgba(0, 81, 255, 0.4); 
            user-select: none;
        }

        .cart-toggle-btn {
            background-color: var(--blanco);
            color: var(--azul-relampago);
            border: none;
            padding: 10px 15px;
            font-size: 1rem;
            font-weight: bold;
            border-radius: 6px;
            cursor: pointer;
            transition: transform 0.2s ease, box-shadow 0.2s ease;
        }

        .cart-toggle-btn:hover {
            transform: scale(1.05);
            box-shadow: 0 0 10px rgba(255, 255, 255, 0.5);
        }

        /* Banner de Bienvenida */
        .welcome-banner {
            background-color: var(--blanco);
            border: 3px solid var(--azul-relampago);
            border-radius: 16px;
            padding: 30px 20px;
            margin-top: 30px;
            text-align: center;
            max-width: 900px;
            width: 90%;
            box-shadow: 0 10px 30px rgba(0, 81, 255, 0.15);
            box-sizing: border-box;
        }

        .banner-logo-container {
            cursor: pointer;
            display: inline-block;
            margin-bottom: 20px;
            user-select: none;
            transition: transform 0.2s ease;
        }

        .banner-logo-container:hover {
            transform: scale(1.02);
        }

        .banner-logo-svg {
            width: 140px;
            height: auto;
            max-width: 100%;
        }

        #banner-card-slide {
            transition: transform 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            transform-origin: top center;
        }

        /* Badges de Colecciones */
        .banner-badges-container {
            margin-top: 25px;
            display: flex;
            justify-content: center;
            gap: 12px;
            flex-wrap: wrap;
        }

        .banner-badge {
            background-color: var(--azul-fondo);
            color: var(--azul-relampago);
            padding: 8px 16px;
            border-radius: 20px;
            font-weight: bold;
            font-size: 0.9rem;
            border: 1.5px solid var(--azul-relampago);
            transition: background-color 0.2s ease, color 0.2s ease, transform 0.2s ease;
            cursor: default;
            user-select: none;
        }

        .banner-badge:hover {
            background-color: var(--azul-relampago);
            color: var(--blanco);
            transform: translateY(-2px);
        }

        .section-title {
            width: 100%;
            text-align: center;
            color: var(--azul-relampago);
            font-size: 2.2rem;
            margin-top: 40px;
            margin-bottom: 10px;
            text-transform: uppercase;
            letter-spacing: 2px;
            font-weight: 800;
            text-shadow: 2px 2px 4px rgba(0, 81, 255, 0.1);
        }

        .store-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 30px;
            padding: 20px 20px 50px 20px; 
            max-width: 1200px;
            width: 100%;
            box-sizing: border-box;
        }

        /* Tarjeta de Producto */
        .product-card {
            background-color: var(--blanco);
            border: 3px solid var(--azul-relampago);
            border-radius: 12px;
            width: 290px;
            padding: 20px;
            box-shadow: 0 0 15px rgba(0, 81, 255, 0.4); 
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            display: flex;
            flex-direction: column;
            box-sizing: border-box;
        }

        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 0 25px rgba(0, 81, 255, 0.8);
        }

        .product-title {
            color: var(--azul-relampago);
            font-size: 1.4rem;
            margin-top: 0;
            text-align: center;
            border-bottom: 2px dashed var(--azul-fondo);
            padding-bottom: 10px;
            margin-bottom: 15px;
        }

        .product-img, .product-video {
            width: 100%;
            height: 200px;
            object-fit: cover;
            border-radius: 8px;
            border: 1px solid #cbd5e1;
            display: block;
        }

        /* Carrusel de Imágenes */
        .carousel-container {
            position: relative;
            width: 100%;
            margin-bottom: 15px;
            height: 200px;
            background-color: #000000;
            border-radius: 8px;
            overflow: hidden;
        }

        .carousel-btn {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            background-color: rgba(0, 81, 255, 0.8);
            color: white;
            border: none;
            width: 30px;
            height: 30px;
            border-radius: 50%;
            cursor: pointer;
            font-weight: bold;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: background-color 0.3s ease;
            z-index: 10;
        }

        .carousel-btn:hover {
            background-color: #003cc2;
        }

        .carousel-btn.left { left: 5px; }
        .carousel-btn.right { right: 5px; }

        .form-group {
            margin-bottom: 15px;
            display: flex;
            flex-direction: column;
        }

        label {
            font-weight: bold;
            margin-bottom: 5px;
            font-size: 0.9rem;
        }

        input[type="text"], select {
            padding: 8px;
            border: 1px solid #cbd5e1;
            border-radius: 6px;
            outline: none;
            font-family: inherit;
        }

        input[type="text"]:focus, select:focus {
            border-color: var(--azul-relampago);
            box-shadow: 0 0 5px rgba(0, 81, 255, 0.3);
        }

        /* Vista previa de carga de archivos (Diseño de subida interactivo al centro) */
        .preview-box {
            width: 100%;
            height: 150px;
            border: 2px dashed var(--azul-relampago);
            border-radius: 8px;
            margin-top: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            background-color: var(--gris-claro);
            overflow: hidden;
            cursor: pointer;
            transition: background-color 0.2s ease, border-color 0.2s ease, transform 0.1s ease;
        }

        .preview-box:hover {
            background-color: rgba(0, 81, 255, 0.05);
            border-color: #003cc2;
            transform: scale(1.01);
        }

        .preview-box:active {
            transform: scale(0.99);
        }

        .preview-box img {
            width: 100%;
            height: 100%;
            object-fit: contain;
        }

        .preview-text-empty {
            font-size: 1rem;
            color: var(--azul-relampago);
            font-weight: bold;
            text-align: center;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            gap: 8px;
            user-select: none;
        }

        .price {
            font-size: 1.8rem;
            font-weight: bold;
            color: var(--azul-relampago);
            text-align: center;
            margin: 15px 0;
            text-shadow: 1px 1px 2px rgba(0, 81, 255, 0.2);
        }

        .buy-btn {
            background-color: var(--azul-relampago);
            color: var(--blanco);
            border: none;
            padding: 12px;
            font-size: 1rem;
            font-weight: bold;
            border-radius: 6px;
            cursor: pointer;
            margin-top: auto;
            transition: background-color 0.3s ease, transform 0.1s ease;
            width: 100%;
        }

        .buy-btn:hover { background-color: #003cc2; }
        .buy-btn:active { transform: scale(0.95); }

        /* Opiniones */
        .reviews-section {
            max-width: 1200px;
            width: 100%;
            padding: 40px 20px 20px 20px;
            box-sizing: border-box;
            text-align: center;
        }

        .reviews-section h2 {
            color: var(--azul-relampago);
            font-size: 2rem;
            margin-bottom: 30px;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .reviews-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px;
        }

        .review-card {
            background-color: var(--blanco);
            border: 2px solid var(--azul-relampago);
            border-radius: 10px;
            padding: 20px;
            width: 300px;
            box-shadow: 0 4px 10px rgba(0, 81, 255, 0.1);
            text-align: left;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .review-card:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(0, 81, 255, 0.3);
        }

        .review-header {
            display: flex;
            align-items: center;
            margin-bottom: 10px;
        }

        .review-avatar {
            width: 45px;
            height: 45px;
            background-color: var(--azul-fondo);
            color: var(--azul-relampago);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 1.2rem;
            margin-right: 12px;
            border: 2px solid var(--azul-relampago);
        }

        .reviewer-name {
            font-weight: bold;
            font-size: 1rem;
            margin: 0;
        }

        .review-stars {
            color: var(--amarillo-estrella);
            font-size: 1.1rem;
            margin-bottom: 10px;
        }

        .review-text {
            font-style: italic;
            color: #475569;
            margin: 0;
            font-size: 0.95rem;
            line-height: 1.4;
        }

        /* Sección de Preguntas Frecuentes (FAQs Acordeón) */
        .faqs-section {
            max-width: 900px;
            width: 90%;
            margin: 40px auto;
            background-color: var(--blanco);
            border: 3px solid var(--azul-relampago);
            border-radius: 16px;
            padding: 30px;
            box-shadow: 0 10px 30px rgba(0, 81, 255, 0.1);
            box-sizing: border-box;
        }

        .faqs-section h2 {
            color: var(--azul-relampago);
            text-align: center;
            font-size: 1.8rem;
            margin-top: 0;
            margin-bottom: 25px;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .faq-accordion {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .faq-item {
            border: 1px solid #cbd5e1;
            border-radius: 8px;
            overflow: hidden;
            transition: border-color 0.3s;
        }

        .faq-item:hover {
            border-color: var(--azul-relampago);
        }

        .faq-question {
            background-color: var(--gris-claro);
            padding: 15px 20px;
            font-weight: bold;
            font-size: 1rem;
            cursor: pointer;
            display: flex;
            justify-content: space-between;
            align-items: center;
            user-select: none;
            transition: background-color 0.3s;
        }

        .faq-question:hover {
            background-color: #e2e8f0;
        }

        .faq-icon {
            font-size: 1.2rem;
            color: var(--azul-relampago);
            transition: transform 0.3s;
        }

        .faq-answer {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.3s ease-out;
            background-color: var(--blanco);
        }

        .faq-answer p {
            padding: 15px 20px;
            margin: 0;
            font-size: 0.95rem;
            line-height: 1.5;
            color: #475569;
        }

        .faq-item.active .faq-answer {
            max-height: 300px; 
        }

        .faq-item.active .faq-icon {
            transform: rotate(45deg);
        }

        /* Carrito Lateral */
        .cart-sidebar {
            position: fixed;
            top: 0;
            right: -400px;
            width: 340px;
            height: 100vh;
            background-color: var(--blanco);
            box-shadow: -5px 0 15px rgba(0, 0, 0, 0.2);
            transition: right 0.4s ease; 
            z-index: 999;
            padding: 20px;
            box-sizing: border-box;
            display: flex;
            flex-direction: column;
        }

        .cart-sidebar.abierto { right: 0; }

        .close-cart-btn {
            background: none;
            border: none;
            color: #ef4444;
            font-size: 1rem;
            font-weight: bold;
            text-align: right;
            cursor: pointer;
            margin-bottom: 10px;
        }

        .cart-sidebar h2 {
            margin-top: 0;
            color: var(--azul-relampago);
            text-align: center;
            border-bottom: 2px dashed var(--azul-fondo);
            padding-bottom: 10px;
        }

        .cart-items {
            list-style: none;
            padding: 0;
            margin: 0 0 15px 0;
            overflow-y: auto;
            flex-grow: 1; 
        }

        .cart-item {
            background-color: var(--gris-claro);
            padding: 12px;
            border-radius: 8px;
            margin-bottom: 10px;
            font-size: 0.85rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-left: 4px solid var(--azul-relampago);
            position: relative;
        }

        .cart-item-details { 
            display: flex; 
            flex-direction: column; 
            padding-right: 20px;
        }

        .cart-item-delete {
            position: absolute;
            top: 8px;
            right: 8px;
            background: none;
            border: none;
            color: #ef4444;
            font-weight: bold;
            cursor: pointer;
            font-size: 0.9rem;
        }

        /* Alertas de Promociones / Packs de Descuentos en el Carrito */
        .promo-discount-badge {
            font-size: 0.8rem;
            padding: 8px;
            border-radius: 6px;
            text-align: center;
            font-weight: bold;
            margin-bottom: 12px;
            transition: all 0.2s ease;
        }

        .promo-badge-info {
            background-color: #fffbeb;
            color: #b45309;
            border: 1.5px solid #fde68a;
        }

        .promo-badge-success {
            background-color: #ecfdf5;
            color: #047857;
            border: 1.5px solid #a7f3d0;
        }

        /* Desglose de Gastos en Carrito */
        .cart-summary-lines {
            border-top: 2px solid var(--azul-fondo);
            padding-top: 15px;
            margin-bottom: 10px;
            display: flex;
            flex-direction: column;
            gap: 6px;
        }

        .cart-summary-line {
            display: flex;
            justify-content: space-between;
            font-size: 0.9rem;
            color: #475569;
        }

        .shipping-free-alert {
            font-size: 0.78rem;
            color: #047857;
            background-color: #ecfdf5;
            padding: 4px 8px;
            border-radius: 4px;
            font-weight: bold;
            text-align: center;
            margin-bottom: 10px;
        }

        .cart-total {
            font-size: 1.5rem;
            font-weight: bold;
            text-align: right;
            margin-bottom: 15px;
            color: var(--texto-oscuro);
            display: flex;
            justify-content: space-between;
        }

        .empty-cart-msg {
            text-align: center;
            color: #94a3b8;
            font-style: italic;
            margin-top: 40px;
        }

        /* Toasts Modernos */
        .toast-container {
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: 1050;
            display: flex;
            flex-direction: column;
            gap: 10px;
            max-width: 350px;
            width: 90%;
        }

        .toast {
            background-color: #1e293b;
            color: #ffffff;
            padding: 15px 20px;
            border-radius: 8px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
            border-left: 5px solid var(--azul-relampago);
            font-size: 0.95rem;
            font-weight: 500;
            display: flex;
            align-items: center;
            justify-content: space-between;
            opacity: 0;
            transform: translateY(20px);
            animation: slideIn 0.3s forwards, fadeOut 0.3s 3.5s forwards;
        }

        .toast.toast-error { border-left-color: #ef4444; }
        .toast.toast-success { border-left-color: #10b981; }

        @keyframes slideIn { to { opacity: 1; transform: translateY(0); } }
        @keyframes fadeOut { to { opacity: 0; transform: translateY(-20px); display: none; } }

        /* MODAL DE CHECKOUT / PAGO */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(15, 23, 42, 0.6);
            backdrop-filter: blur(4px);
            display: none;
            align-items: center;
            justify-content: center;
            z-index: 1001;
            padding: 20px;
            box-sizing: border-box;
        }

        .modal-overlay.activo { display: flex; }

        .checkout-modal {
            background-color: var(--blanco);
            border: 3px solid var(--azul-relampago);
            border-radius: 16px;
            width: 100%;
            max-width: 500px;
            max-height: 90vh;
            overflow-y: auto;
            padding: 25px;
            box-shadow: 0 20px 25px -5px rgba(0, 81, 255, 0.3);
            box-sizing: border-box;
            position: relative;
        }

        .close-modal-btn {
            position: absolute;
            top: 15px;
            right: 15px;
            background: none;
            border: none;
            color: #ef4444;
            font-size: 1.2rem;
            font-weight: bold;
            cursor: pointer;
        }

        .checkout-modal h2 {
            margin-top: 0;
            color: var(--azul-relampago);
            text-align: center;
            border-bottom: 2px dashed var(--azul-fondo);
            padding-bottom: 12px;
            font-size: 1.6rem;
        }

        /* Caja de Resumen Visual en Checkout */
        .checkout-summary-box {
            background-color: var(--gris-claro);
            border-radius: 10px;
            padding: 15px;
            margin-bottom: 20px;
            border: 1.5px solid #cbd5e1;
        }

        .checkout-summary-box h3 {
            margin: 0 0 10px 0;
            font-size: 1rem;
            color: var(--azul-relampago);
            text-transform: uppercase;
            letter-spacing: 0.5px;
            border-bottom: 1px solid #cbd5e1;
            padding-bottom: 5px;
        }

        .chk-summary-items {
            display: flex;
            flex-direction: column;
            gap: 8px;
            margin-bottom: 10px;
        }

        .chk-item-line {
            display: flex;
            justify-content: space-between;
            font-size: 0.85rem;
            line-height: 1.4;
        }

        .chk-total-row {
            display: flex;
            justify-content: space-between;
            font-weight: bold;
            font-size: 1.1rem;
            border-top: 2.5px solid #cbd5e1;
            padding-top: 10px;
            margin-top: 5px;
        }

        .payment-method-selector {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }

        .payment-option {
            flex: 1;
            border: 2px solid var(--azul-fondo);
            border-radius: 8px;
            padding: 12px;
            text-align: center;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.2s ease;
        }

        .payment-option.selected {
            border-color: var(--azul-relampago);
            background-color: rgba(0, 81, 255, 0.05);
            color: var(--azul-relampago);
        }

        .info-box {
            background-color: var(--gris-claro);
            border-left: 4px solid var(--azul-relampago);
            padding: 12px;
            border-radius: 4px;
            font-size: 0.9rem;
            margin-bottom: 15px;
            line-height: 1.4;
        }

        .info-box strong { color: var(--azul-relampago); }

        .whatsapp-submit-btn {
            background-color: var(--verde-whatsapp);
            color: white;
            border: none;
            padding: 14px;
            border-radius: 8px;
            font-size: 1.1rem;
            font-weight: bold;
            width: 100%;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            transition: transform 0.2s, background-color 0.2s;
            margin-top: 15px;
        }

        .whatsapp-submit-btn:hover {
            background-color: #1ebe57;
            transform: scale(1.02);
        }

        /* Pie de página */
        footer {
            background-color: var(--texto-oscuro);
            color: var(--blanco);
            width: 100%;
            text-align: center;
            padding: 30px 20px;
            margin-top: auto; 
            box-sizing: border-box;
            border-top: 4px solid var(--azul-relampago);
        }

        footer h3 {
            margin: 0 0 10px 0;
            color: var(--azul-fondo);
            font-size: 1.5rem;
        }

        .footer-contact-item {
            margin: 10px 0;
            font-size: 1.1rem;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-wrap: wrap;
            gap: 10px;
        }

        footer a {
            color: var(--blanco);
            text-decoration: none;
            font-weight: bold;
            background-color: var(--azul-relampago);
            padding: 5px 15px;
            border-radius: 6px;
            transition: background-color 0.3s ease, transform 0.2s ease;
            display: inline-block;
        }

        footer a:hover {
            background-color: #003cc2;
            transform: scale(1.05);
        }
    </style>
</head>
<body>

    <!-- Contenedor global de Toasts -->
    <div id="toast-container" class="toast-container"></div>

    <header>
        <div class="header-content">
            <div class="header-logo-container">
                <svg viewBox="0 0 100 80" class="header-logo-svg">
                    <rect x="15" y="15" width="70" height="50" rx="6" fill="#ffffff" stroke="#0051ff" stroke-width="2" />
                    <rect x="22" y="2" width="56" height="40" rx="4" fill="#0051ff" />
                    <path d="M 15,35 L 85,35" stroke="#0051ff" stroke-width="1.5" />
                    <text x="50" y="52" font-family="sans-serif" font-weight="900" font-size="16" fill="#0051ff" text-anchor="middle">W</text>
                </svg>
                <h1>Wallman Store</h1>
            </div>
            <button class="cart-toggle-btn" onclick="toggleCarrito()">🛒 Carrito (<span id="cart-count">0</span>)</button>
        </div>
    </header>

    <!-- Cartel de Bienvenida -->
    <div class="welcome-banner">
        <div class="banner-logo-container" onclick="slideCardBanner()">
            <svg viewBox="0 0 100 80" class="banner-logo-svg">
                <rect x="15" y="15" width="70" height="50" rx="6" fill="#1e293b" stroke="#0051ff" stroke-width="2" />
                <rect id="banner-card-slide" x="22" y="2" width="56" height="40" rx="4" fill="#0051ff" />
                <path d="M 15,35 L 85,35" stroke="#0051ff" stroke-width="1.5" />
                <text x="50" y="52" font-family="'Segoe UI', sans-serif" font-weight="900" font-size="16" fill="#ffffff" text-anchor="middle">W</text>
                <path d="M 42,39 L 44,43 L 50,40 L 56,43 L 58,39 L 55,41 L 50,37 L 45,41 Z" fill="#f59e0b" />
            </svg>
            <div style="font-size: 0.85rem; color: var(--azul-relampago); font-weight: bold; margin-top: 5px;">¡Haz clic para deslizar la tarjeta!</div>
        </div>

        <h2 style="font-size: 2.2rem; margin: 0 0 10px 0; color: var(--azul-relampago); font-weight: 800; text-transform: uppercase;">Bienvenido a Wallman Store</h2>
        <p style="font-size: 1.2rem; color: #475569; max-width: 700px; line-height: 1.6; margin: 0 auto; margin-top: 15px;">
            Carteras premium de diseño elegante, compactas y funcionales, creadas para llevar lo esencial con estilo.
        </p>

        <!-- Etiquetas de las colecciones -->
        <div class="banner-badges-container">
            <span class="banner-badge">Colección Silueta</span>
            <span class="banner-badge">Cartera Mémoire</span>
            <span class="banner-badge">Lettre Royale</span>
            <span class="banner-badge">Cartera Galerie</span>
            <span class="banner-badge">Monedero Grand</span>
        </div>
    </div>

    <h2 class="section-title">Nuestras Colecciones</h2>

    <!-- Sección de Productos -->
    <main class="store-container">

        <!-- Producto 1: Colección Silueta -->
        <div class="product-card">
            <h2 class="product-title">Colección Silueta</h2>
            <div class="carousel-container">
                <button class="carousel-btn left" onclick="cambiarFotoSilueta(-1)">&#10094;</button>
                <img src="https://img.kwcdn.com/product/fancy/6bbbd317-8897-4fc4-93ce-4b6a52ac490c.jpg?imageView2/2/w/800/q/70/format/avif" alt="Colección Silueta" class="product-img" id="img-silueta">
                <button class="carousel-btn right" onclick="cambiarFotoSilueta(1)">&#10095;</button>
            </div>
            <div class="form-group">
                <!-- Selector de archivos oculto triggered por clic en la preview-box -->
                <input type="file" id="dibujo-silueta" accept="image/*" onchange="mostrarVistaPrevia(this, 'preview-silueta')" style="display: none;">
                <div class="preview-box" id="preview-silueta" onclick="document.getElementById('dibujo-silueta').click()">
                    <span class="preview-text-empty">
                        <svg viewBox="0 0 24 24" style="width:28px; height:28px; fill:var(--azul-relampago); margin-bottom: 4px;"><path d="M19 13h-6v6h-2v-6H5v-2h6V5h2v6h6v2z"/></svg>
                        Añadir imagen
                    </span>
                </div>
            </div>
            <div class="form-group">
                <label for="color-silueta">Color de la cartera:</label>
                <select id="color-silueta">
                    <option value="Negro">Negro</option>
                    <option value="Marrón">Marrón</option>
                </select>
            </div>
            <div class="price">8,99 €</div>
            <button class="buy-btn" onclick="agregarAlCarrito('silueta', 8.99)">Añadir al carrito</button>
        </div>

        <!-- Producto 2: Cartera Memoire -->
        <div class="product-card">
            <h2 class="product-title">Cartera Mémoire</h2>
            <div class="carousel-container">
                <button class="carousel-btn left" onclick="cambiarFotoMemoire(-1)">&#10094;</button>
                <img src="https://img.kwcdn.com/product/fancy/2f3041dc-870c-4f20-9d29-24254276b7f5.jpg?imageView2/2/w/800/q/70/format/avif" alt="Cartera Memoire" class="product-img" id="img-memoire">
                <button class="carousel-btn right" onclick="cambiarFotoMemoire(1)">&#10095;</button>
            </div>
            <div class="form-group">
                <input type="file" id="foto-memoire" accept="image/*" onchange="mostrarVistaPrevia(this, 'preview-memoire')" style="display: none;">
                <div class="preview-box" id="preview-memoire" onclick="document.getElementById('foto-memoire').click()">
                    <span class="preview-text-empty">
                        <svg viewBox="0 0 24 24" style="width:28px; height:28px; fill:var(--azul-relampago); margin-bottom: 4px;"><path d="M19 13h-6v6h-2v-6H5v-2h6V5h2v6h6v2z"/></svg>
                        Añadir imagen
                    </span>
                </div>
            </div>
            <div class="form-group">
                <label for="color-memoire">Color de la cartera:</label>
                <select id="color-memoire">
                    <option value="Negro">Negro</option>
                </select>
            </div>
            <div class="price">7,99 €</div>
            <button class="buy-btn" onclick="agregarAlCarrito('memoire', 7.99)">Añadir al carrito</button>
        </div>

        <!-- Producto 3: Lettre Royale -->
        <div class="product-card">
            <h2 class="product-title">Lettre Royale</h2>
            <div class="carousel-container" id="carousel-nombre-box">
                <button class="carousel-btn left" onclick="cambiarMediaNombre(-1)">&#10094;</button>
                <div id="media-nombre-content"></div>
                <button class="carousel-btn right" onclick="cambiarMediaNombre(1)">&#10095;</button>
            </div>
            <div class="form-group">
                <label for="letra-principal">Letra principal (Inicial grande):</label>
                <input type="text" id="letra-principal" maxlength="1" placeholder="Ej. D" style="text-transform: uppercase;">
            </div>
            <div class="form-group">
                <label for="solo-nombre">Nombre grabado:</label>
                <input type="text" id="solo-nombre" placeholder="Ej. David">
            </div>
            <div class="form-group">
                <label for="color-solo-nombre">Color de la cartera:</label>
                <select id="color-solo-nombre">
                    <option value="Negro">Negro</option>
                    <option value="Marrón">Marrón</option>
                    <option value="Marrón Oscuro">Marrón Oscuro</option>
                </select>
            </div>
            <div class="price">7,99 €</div>
            <button class="buy-btn" onclick="agregarAlCarrito('con-nombre', 7.99)">Añadir al carrito</button>
        </div>

        <!-- Producto 4: Cartera Galerie -->
        <div class="product-card">
            <h2 class="product-title">Cartera Galerie</h2>
            <div class="carousel-container">
                <button class="carousel-btn left" onclick="cambiarFotoImgColor(-1)">&#10094;</button>
                <img src="https://img.kwcdn.com/product/fancy/042aa119-52c2-48e8-9b5f-fb12d624016d.jpg?imageView2/2/w/800/q/70/format/avif" alt="Cartera Galerie" class="product-img" id="img-cartera-color">
                <button class="carousel-btn right" onclick="cambiarFotoImgColor(1)">&#10095;</button>
            </div>
            <div class="form-group">
                <input type="file" id="img-cartera" accept="image/*" onchange="mostrarVistaPrevia(this, 'preview-cartera-color')" style="display: none;">
                <div class="preview-box" id="preview-cartera-color" onclick="document.getElementById('img-cartera').click()">
                    <span class="preview-text-empty">
                        <svg viewBox="0 0 24 24" style="width:28px; height:28px; fill:var(--azul-relampago); margin-bottom: 4px;"><path d="M19 13h-6v6h-2v-6H5v-2h6V5h2v6h6v2z"/></svg>
                        Añadir imagen
                    </span>
                </div>
            </div>
            <div class="form-group">
                <label for="color-cartera-img">Color de la cartera:</label>
                <select id="color-cartera-img">
                    <option value="Negro">Negro</option>
                    <option value="Marrón">Marrón</option>
                </select>
            </div>
            <div class="price">9,99 €</div>
            <button class="buy-btn" onclick="agregarAlCarrito('cartera-img', 9.99)">Añadir al carrito</button>
        </div>

        <!-- Producto 5: Monedero Grand -->
        <div class="product-card">
            <h2 class="product-title">Monedero Grand</h2>
            <div class="carousel-container">
                <button class="carousel-btn left" onclick="cambiarFotoMonedero(-1)">&#10094;</button>
                <img src="https://img.kwcdn.com/product/fancy/88aa4ac3-fffe-4241-85d3-92b7521e6c8d.jpg?imageView2/2/w/800/q/70/format/avif" alt="Monedero Grand" class="product-img" id="img-monedero-color">
                <button class="carousel-btn right" onclick="cambiarFotoMonedero(1)">&#10095;</button>
            </div>
            <div class="form-group">
                <input type="file" id="img-monedero" accept="image/*" onchange="mostrarVistaPrevia(this, 'preview-monedero')" style="display: none;">
                <div class="preview-box" id="preview-monedero" onclick="document.getElementById('img-monedero').click()">
                    <span class="preview-text-empty">
                        <svg viewBox="0 0 24 24" style="width:28px; height:28px; fill:var(--azul-relampago); margin-bottom: 4px;"><path d="M19 13h-6v6h-2v-6H5v-2h6V5h2v6h6v2z"/></svg>
                        Añadir imagen
                    </span>
                </div>
            </div>
            <div class="price">24,99 €</div>
            <button class="buy-btn" onclick="agregarAlCarrito('monedero-img', 24.99)">Añadir al carrito</button>
        </div>

    </main>

    <!-- Sección de Preguntas Frecuentes (FAQs Acordeón) -->
    <section class="faqs-section">
        <h2>💬 Preguntas Frecuentes</h2>
        <div class="faq-accordion">
            <div class="faq-item">
                <div class="faq-question" onclick="toggleFaq(this)">
                    <span>¿Cuánto tarda en fabricarse y llegar mi pedido?</span>
                    <span class="faq-icon">+</span>
                </div>
                <div class="faq-answer">
                    <p>Cada una de nuestras carteras personalizadas se prepara individualmente con grabado láser. El proceso de fabricación toma una semana. Una vez enviada, el tiempo total de entrega estimado es de 18 días laborables.</p>
                </div>
            </div>
            <div class="faq-item">
                <div class="faq-question" onclick="toggleFaq(this)">
                    <span>¿Se puede devolver un producto personalizado?</span>
                    <span class="faq-icon">+</span>
                </div>
                <div class="faq-answer">
                    <p>Al ser artículos totalmente personalizados con tus nombres, iniciales o fotografías exclusivas, no es posible cancelarlos o devolverlos una vez fabricados, salvo que presenten algún defecto de fabricación.</p>
                </div>
            </div>
            <div class="faq-item">
                <div class="faq-question" onclick="toggleFaq(this)">
                    <span>¿El grabado se borra con el tiempo?</span>
                    <span class="faq-icon">+</span>
                </div>
                <div class="faq-answer">
                    <p>¡Para nada! Utilizamos grabado láser premium de alta precisión que quema suavemente la superficie del cuero sintético, creando un relieve permanente e imborrable que resiste perfectamente al desgaste diario.</p>
                </div>
            </div>
            <div class="faq-item">
                <div class="faq-question" onclick="toggleFaq(this)">
                    <span>¿Cómo os envío mi fotografía para el grabado?</span>
                    <span class="faq-icon">+</span>
                </div>
                <div class="faq-answer">
                    <p>¡Es facilísimo! La web te permite subirla de forma temporal para ver cómo queda. Al tramitar el pedido por WhatsApp, solo tienes que pulsar el botón de adjuntar (clip o cámara de fotos) en el chat de WhatsApp de forma nativa usando el clip 📎 o la cámara 📷 y enviarnos el mismo archivo.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Sección de Reseñas -->
    <section class="reviews-section">
        <h2>💬 Opiniones de nuestros clientes</h2>
        <div class="reviews-container">
            <div class="review-card">
                <div class="review-header">
                    <div class="review-avatar">A</div>
                    <p class="reviewer-name">Alejandro M.</p>
                </div>
                <div class="review-stars">⭐⭐⭐⭐⭐</div>
                <p class="review-text">"Compré la Cartera Mémoire con la imagen de mi perro y es una pasada. Súper recomendable."</p>
            </div>
            <div class="review-card">
                <div class="review-header">
                    <div class="review-avatar">M</div>
                    <p class="reviewer-name">María T.</p>
                </div>
                <div class="review-stars">⭐⭐⭐⭐⭐</div>
                <p class="review-text">"Pedí la Colección Silueta en color marrón para el día del padre. El grabado viene súper bien definido. Llegó rapidísimo, 100% recomendados."</p>
            </div>
            <div class="review-card">
                <div class="review-header">
                    <div class="review-avatar">C</div>
                    <p class="reviewer-name">Carlos G.</p>
                </div>
                <div class="review-stars">⭐⭐⭐⭐⭐</div>
                <p class="review-text">"El Monedero Grand es una pasada, la foto a color se ve súper nítida. El sistema del carrito es muy cómodo. Volveré a comprar seguro."</p>
            </div>
        </div>
    </section>

    <!-- Zona de Contacto / Pie de Página -->
    <footer>
        <h3>¿Tienes alguna duda o petición especial? ¡Contáctanos!</h3>
        <div class="footer-contact-item">
            <span>Email:</span>
            <a href="mailto:wallmanstore@gmail.com">wallmanstore@gmail.com</a>
        </div>
        <div class="footer-contact-item" style="width: 100%; margin-top: 10px;">
            <span>Teléfono / WhatsApp:</span>
            <a href="tel:679016477">679 01 64 77</a>
        </div>
    </footer>

    <!-- Zona del Carrito Lateral -->
    <aside class="cart-sidebar" id="carrito-lateral">
        <button class="close-cart-btn" onclick="toggleCarrito()">✖ Cerrar</button>
        <h2>🛒 Tu Carrito</h2>
        
        <!-- Indicador de Descuentos Dinámico (Opción 3) -->
        <div id="promo-badge-container"></div>
        
        <div id="mensaje-vacio" class="empty-cart-msg">Tu carrito está vacío</div>
        <ul class="cart-items" id="lista-carrito"></ul>

        <!-- Desglose de Gastos de Envío -->
        <div class="cart-summary-lines" id="cart-summary-area" style="display: none;">
            <div class="cart-summary-line">
                <span>Subtotal:</span>
                <span><span id="subtotal-precio">0.00</span> €</span>
            </div>
            <!-- Descuento por Volumen (Oculto si es 0) -->
            <div class="cart-summary-line" id="discount-summary-line" style="display: none; color: #ef4444; font-weight: bold;">
                <span>Descuento aplicado:</span>
                <span>-<span id="discount-value">0.00</span> €</span>
            </div>
            <div class="cart-summary-line">
                <span>Envío certificado:</span>
                <span id="shipping-fee-text">3.99 €</span>
            </div>
            <div class="shipping-free-alert" id="free-shipping-alert">
                ¡Añade más para envío gratis (Mínimo 30 €)!
            </div>
            <div class="cart-total">
                <span>Total:</span>
                <span><span id="total-precio">0.00</span> €</span>
            </div>
        </div>

        <button class="buy-btn" id="checkout-trigger-btn" onclick="finalizarCompra()" style="display: none;">Tramitar Pedido</button>
    </aside>

    <!-- Modal de Envío y Pago -->
    <div class="modal-overlay" id="checkout-modal-overlay">
        <div class="checkout-modal">
            <button class="close-modal-btn" onclick="cerrarCheckout()">✕</button>
            <h2>📦 Datos de Envío</h2>
            
            <!-- Resumen Visual Detallado del Checkout -->
            <div class="checkout-summary-box">
                <h3>Resumen de la Compra</h3>
                <div class="chk-summary-items" id="checkout-items-list"></div>
                <div class="chk-item-line" style="margin-top: 10px;">
                    <span>Subtotal Productos:</span>
                    <span id="checkout-subtotal-val">0.00 €</span>
                </div>
                <!-- Descuento en Checkout -->
                <div class="chk-item-line" id="checkout-discount-row" style="display: none; color: #ef4444; font-weight: bold;">
                    <span>Descuento aplicado:</span>
                    <span id="checkout-discount-val">-0.00 €</span>
                </div>
                <div class="chk-item-line">
                    <span>Envío certificado:</span>
                    <span id="checkout-shipping-val">3.99 €</span>
                </div>
                <div class="chk-total-row">
                    <span>Total a Pagar:</span>
                    <span id="checkout-total-val">0.00 €</span>
                </div>
            </div>

            <form id="checkout-form" onsubmit="procesarPedido(event)">
                <div class="form-group">
                    <label for="order-name">Nombre y Apellidos *</label>
                    <input type="text" id="order-name" required placeholder="Ej. Juan Pérez">
                </div>
                <div class="form-group">
                    <label for="order-address">Dirección de Envío Completa *</label>
                    <input type="text" id="order-address" required placeholder="Calle, Número, Piso, Código Postal, Ciudad">
                </div>
                <div class="form-group">
                    <label for="order-phone">Teléfono de Contacto *</label>
                    <input type="text" id="order-phone" required placeholder="Ej. 600000000">
                </div>

                <label>Método de Pago Preferido *</label>
                <div class="payment-method-selector">
                    <div class="payment-option selected" id="opt-bizum" onclick="selectPayment('Bizum')">
                        📱 Bizum
                    </div>
                    <div class="payment-option" id="opt-transfer" onclick="selectPayment('Transferencia')">
                        🏦 Transferencia
                    </div>
                </div>

                <div class="info-box" id="payment-instructions">
                    Realizarás un <strong>Bizum rápido y seguro al 679 01 64 77</strong> tras confirmar el pedido. En el chat de WhatsApp te facilitaremos el concepto y coordinaremos las imágenes personalizadas.
                </div>

                <div class="info-box" style="background-color: #fffbeb; border-left-color: #f59e0b;">
                    ⚠️ <strong>¿CÓMO ENVIAR TUS FOTOS?</strong> Como tu pedido tiene carteras personalizadas, al pulsar el botón de abajo **también podrás adjuntar directamente las fotos o dibujos** desde tu galería en el propio chat de WhatsApp de forma nativa usando el clip 📎 o la cámara 📷.
                </div>

                <button type="submit" class="whatsapp-submit-btn">
                    <span>💬 Confirmar y Enviar por WhatsApp</span>
                </button>
            </form>
        </div>
    </div>

    <!-- Código de Script / Lógica de la Web -->
    <script>
        // Declaración de variables globales
        let itemsCarrito = [];
        let total = 0;
        let subtotal = 0;
        let costeEnvio = 3.99;
        let descuentoPorcentaje = 0;
        let descuentoValor = 0;
        let subtotalConDescuento = 0;
        let metodoPagoSeleccionado = 'Bizum';

        // Al iniciar, cargar datos persistidos de LocalStorage si existen
        window.onload = function() {
            const savedCart = localStorage.getItem('wallman_cart');
            if (savedCart) {
                try {
                    itemsCarrito = JSON.parse(savedCart);
                    actualizarInterfazCarrito();
                } catch(e) {
                    console.error("Error al cargar el carrito de LocalStorage:", e);
                    itemsCarrito = [];
                }
            }
        };

        // Sistema dinámico de avisos tipo Toast (Evita alertas molestas)
        function showToast(message, type = 'success') {
            const container = document.getElementById('toast-container');
            const toast = document.createElement('div');
            toast.className = `toast toast-${type}`;
            toast.innerHTML = `
                <span>${message}</span>
                <span style="margin-left: 10px; cursor: pointer;" onclick="this.parentElement.remove()">✕</span>
            `;
            container.appendChild(toast);
            
            setTimeout(() => {
                toast.remove();
            }, 3800);
        }

        // Animación del logotipo interactivo del banner
        let tarjetaDeslizada = false;
        function slideCardBanner() {
            const card = document.getElementById('banner-card-slide');
            if (!tarjetaDeslizada) {
                card.style.transform = 'translateY(-12px)';
                tarjetaDeslizada = true;
                showToast("¡Tarjeta deslizada! Lista para pagar.", "success");
            } else {
                card.style.transform = 'translateY(0px)';
                tarjetaDeslizada = false;
            }
        }

        // Control del acordeón FAQs
        function toggleFaq(element) {
            const item = element.parentElement;
            const isActive = item.classList.contains('active');
            
            // Cerrar todos los demás primero
            document.querySelectorAll('.faq-item').forEach(f => f.classList.remove('active'));
            
            // Activar o desactivar el pulsado
            if (!isActive) {
                item.classList.add('active');
            }
        }

        // Vista previa de carga de imágenes (Soportando el nuevo diseño visual)
        function mostrarVistaPrevia(input, idContenedor) {
            const contenedor = document.getElementById(idContenedor);
            if (input.files && input.files[0]) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    contenedor.innerHTML = `<img src="${e.target.result}" alt="Vista previa">`;
                }
                reader.readAsDataURL(input.files[0]);
                showToast("Imagen cargada correctamente. Al tramitar, recuerda enviarla por el chat.", "success");
            } else {
                contenedor.innerHTML = `
                    <span class="preview-text-empty">
                        <svg viewBox="0 0 24 24" style="width:28px; height:28px; fill:var(--azul-relampago); margin-bottom: 4px;"><path d="M19 13h-6v6h-2v-6H5v-2h6V5h2v6h6v2z"/></svg>
                        Añadir imagen
                    </span>`;
            }
        }

        // CARRUSEL - COLECCIÓN SILUETA
        const fotosSilueta = [
            "https://img.kwcdn.com/product/fancy/6bbbd317-8897-4fc4-93ce-4b6a52ac490c.jpg?imageView2/2/w/800/q/70/format/avif",
            "https://img.kwcdn.com/product/fancy/a9057984-2160-4b02-a8af-18289f61da2e.jpg?imageView2/2/w/800/q/70/format/avif",
            "https://img.kwcdn.com/product/fancy/c8f33be3-06ef-45ed-81b1-5b775c8d50c0.jpg?imageView2/2/w/800/q/70/format/avif"
        ];
        let indiceSiluetaActual = 0;

        function cambiarFotoSilueta(direccion) {
            indiceSiluetaActual += direccion;
            if (indiceSiluetaActual >= fotosSilueta.length) indiceSiluetaActual = 0;
            if (indiceSiluetaActual < 0) indiceSiluetaActual = fotosSilueta.length - 1;
            document.getElementById('img-silueta').src = fotosSilueta[indiceSiluetaActual];
        }

        // CARRUSEL - CARTERA MEMOIRE
        const fotosMemoire = [
            "https://img.kwcdn.com/product/fancy/2f3041dc-870c-4f20-9d29-24254276b7f5.jpg?imageView2/2/w/800/q/70/format/avif",
            "https://img.kwcdn.com/product/fancy/92236950-8096-45b6-a0d2-0de9560e7732.jpg?imageView2/2/w/1300/q/90/format/avif",
            "https://img.kwcdn.com/product/fancy/c6d71fed-b057-44a8-bd89-f72b22e637ff.jpg?imageView2/2/w/1300/q/90/format/avif"
        ];
        let indiceMemoireActual = 0;

        function cambiarFotoMemoire(direccion) {
            indiceMemoireActual += direccion;
            if (indiceMemoireActual >= fotosMemoire.length) indiceMemoireActual = 0;
            if (indiceMemoireActual < 0) indiceMemoireActual = fotosMemoire.length - 1;
            document.getElementById('img-memoire').src = fotosMemoire[indiceMemoireActual];
        }

        // CARTERA MULTIMEDIA - LETTRE ROYALE
        const mediaNombre = [
            { tipo: 'imagen', url: 'https://img.kwcdn.com/product/open/edfdd8e645b54d71b30c424bdff236d8-goods.jpeg?imageView2/2/w/800/q/70/format/avif' },
            { tipo: 'imagen', url: 'https://img.kwcdn.com/product/open/7513c8b437ea4bfe9e3077c5158bec40-goods.jpeg?imageView2/2/w/800/q/70/format/avif' },
            { tipo: 'imagen', url: 'https://img.kwcdn.com/product/open/5f86fc214a814379ae98d13c6d7be048-goods.jpeg?imageView2/2/w/800/q/70/format/avif' },
            { tipo: 'video', url: 'https://goods-vod.kwcdn.com/goods-video/844a08467c13774f58a815e8c61c7cd7e7513215gs2CV.f30.mp4' }
        ];
        let indiceMediaNombre = 0;

        function renderMediaNombre() {
            const contenedor = document.getElementById('media-nombre-content');
            const itemActual = mediaNombre[indiceMediaNombre];
            
            if (itemActual.tipo === 'imagen') {
                contenedor.innerHTML = `<img src="${itemActual.url}" alt="Lettre Royale" class="product-img">`;
            } else if (itemActual.tipo === 'video') {
                contenedor.innerHTML = `
                    <video class="product-video" autoplay muted loop playsinline>
                        <source src="${itemActual.url}" type="video/mp4">
                        Tu navegador no soporta vídeos.
                    </video>`;
            }
        }

        function cambiarMediaNombre(direccion) {
            indiceMediaNombre += direccion;
            if (indiceMediaNombre >= mediaNombre.length) indiceMediaNombre = 0;
            if (indiceMediaNombre < 0) indiceMediaNombre = mediaNombre.length - 1;
            renderMediaNombre();
        }
        
        renderMediaNombre();

        // CARRUSEL - CARTERA GALERIE
        const fotosImgColor = [
            "https://img.kwcdn.com/product/fancy/042aa119-52c2-48e8-9b5f-fb12d624016d.jpg?imageView2/2/w/800/q/70/format/avif",
            "https://img.kwcdn.com/product/fancy/38381e9c-b13c-48a4-b0c9-955f4029456c.jpg?imageView2/2/w/1300/q/90/format/avif",
            "https://img.kwcdn.com/product/fancy/33de14de-d311-4ba0-ab12-fba39526662c.jpg?imageView2/2/w/1300/q/90/format/avif"
        ];
        let indiceImgColorActual = 0;

        function cambiarFotoImgColor(direccion) {
            indiceImgColorActual += direccion;
            if (indiceImgColorActual >= fotosImgColor.length) indiceImgColorActual = 0;
            if (indiceImgColorActual < 0) indiceImgColorActual = fotosImgColor.length - 1;
            document.getElementById('img-cartera-color').src = fotosImgColor[indiceImgColorActual];
        }

        // CARRUSEL - MONEDERO GRAND
        const fotosMonedero = [
            "https://img.kwcdn.com/product/fancy/88aa4ac3-fffe-4241-85d3-92b7521e6c8d.jpg?imageView2/2/w/800/q/70/format/avif",
            "https://img.kwcdn.com/product/fancy/66e3ebc5-fc46-47d2-85b6-f475f007e803.jpg?imageView2/2/w/1300/q/90/format/avif",
            "https://img.kwcdn.com/product/fancy/db297399-c81a-4389-bac2-d7ea88b81806.jpg?imageView2/2/w/1300/q/90/format/avif",
            "https://img.kwcdn.com/product/fancy/dc72eaa3-034c-46ec-85a1-acac2cc7f916.jpg?imageView2/2/w/1300/q/90/format/avif"
        ];
        let indiceMonederoActual = 0;

        function cambiarFotoMonedero(direccion) {
            indiceMonederoActual += direccion;
            if (indiceMonederoActual >= fotosMonedero.length) indiceMonederoActual = 0;
            if (indiceMonederoActual < 0) indiceMonederoActual = fotosMonedero.length - 1;
            document.getElementById('img-monedero-color').src = fotosMonedero[indiceMonederoActual];
        }

        // LÓGICA DEL CARRITO CON LOCALSTORAGE Y ENVÍOS
        function toggleCarrito() {
            const carrito = document.getElementById('carrito-lateral');
            carrito.classList.toggle('abierto');
        }

        function agregarAlCarrito(tipo, precio) {
            let nombreArticulo = "";
            let especificaciones = "";

            if (tipo === 'silueta') {
                nombreArticulo = "Colección Silueta";
                let inputImg = document.getElementById('dibujo-silueta');
                let estadoImagen = inputImg.files.length > 0 ? "✅ Sí (Dibujo subido en web)" : "❌ No subido en web";
                let color = document.getElementById('color-silueta').value;
                especificaciones = `Color: ${color} | Dibujo de líneas: ${estadoImagen}`;
            } else if (tipo === 'memoire') {
                nombreArticulo = "Cartera Mémoire";
                let inputImg = document.getElementById('foto-memoire');
                let estadoImagen = inputImg.files.length > 0 ? "✅ Sí (Foto subida en web)" : "❌ No subida en web";
                let color = document.getElementById('color-memoire').value;
                especificaciones = `Color: ${color} | Foto: ${estadoImagen}`;
            } else if (tipo === 'con-nombre') {
                nombreArticulo = "Lettre Royale";
                let inicial = document.getElementById('letra-principal').value.trim().toUpperCase() || "D";
                let nombreGrabado = document.getElementById('solo-nombre').value.trim() || "David";
                let color = document.getElementById('color-solo-nombre').value;
                especificaciones = `Inicial: ${inicial} | Grabado: ${nombreGrabado} | Color: ${color}`;
            } else if (tipo === 'cartera-img') {
                nombreArticulo = "Cartera Galerie";
                let inputImg = document.getElementById('img-cartera');
                let estadoImagen = inputImg.files.length > 0 ? "✅ Sí (Imagen a color subida)" : "❌ No subida en web";
                let color = document.getElementById('color-cartera-img').value;
                especificaciones = `Color: ${color} | Imagen a color: ${estadoImagen}`;
            } else if (tipo === 'monedero-img') {
                nombreArticulo = "Monedero Grand";
                let inputImg = document.getElementById('img-monedero');
                let estadoImagen = inputImg.files.length > 0 ? "✅ Sí (Imagen a color subida)" : "❌ No subida en web";
                especificaciones = `Imagen a color: ${estadoImagen}`;
            }

            // Crear objeto único para el carrito
            const nuevoProducto = {
                id: Date.now() + Math.random().toString(36).substr(2, 5),
                nombre: nombreArticulo,
                especificaciones: especificaciones,
                precio: precio
            };

            itemsCarrito.push(nuevoProducto);
            
            // Guardar en LocalStorage
            localStorage.setItem('wallman_cart', JSON.stringify(itemsCarrito));

            actualizarInterfazCarrito();
            showToast("Artículo añadido al carrito");

            // Abrir automáticamente el panel lateral para dar feedback de compra
            document.getElementById('carrito-lateral').classList.add('abierto');
        }

        function eliminarDelCarrito(idAEliminar) {
            itemsCarrito = itemsCarrito.filter(item => item.id !== idAEliminar);
            localStorage.setItem('wallman_cart', JSON.stringify(itemsCarrito));
            actualizarInterfazCarrito();
            showToast("Artículo eliminado del carrito", "error");
        }

        function actualizarInterfazCarrito() {
            const lista = document.getElementById('lista-carrito');
            const subtotalText = document.getElementById('subtotal-precio');
            const shippingText = document.getElementById('shipping-fee-text');
            const freeShippingAlert = document.getElementById('free-shipping-alert');
            const totalText = document.getElementById('total-precio');
            const cartCount = document.getElementById('cart-count');
            const emptyMsg = document.getElementById('mensaje-vacio');
            const summaryArea = document.getElementById('cart-summary-area');
            const chkBtn = document.getElementById('checkout-trigger-btn');
            
            const promoBadgeContainer = document.getElementById('promo-badge-container');
            const discountSummaryLine = document.getElementById('discount-summary-line');
            const discountValueText = document.getElementById('discount-value');

            lista.innerHTML = "";
            subtotal = 0;

            if (itemsCarrito.length === 0) {
                emptyMsg.style.display = 'block';
                summaryArea.style.display = 'none';
                chkBtn.style.display = 'none';
                promoBadgeContainer.innerHTML = "";
                cartCount.innerText = "0";
                return;
            }

            emptyMsg.style.display = 'none';
            summaryArea.style.display = 'flex';
            chkBtn.style.display = 'block';

            // Listar y acumular subtotal de productos
            itemsCarrito.forEach(item => {
                subtotal += item.precio;
                const li = document.createElement('li');
                li.className = 'cart-item';
                li.innerHTML = `
                    <div class="cart-item-details">
                        <strong>${item.nombre}</strong>
                        <span><small>${item.especificaciones}</small></span>
                    </div>
                    <strong>${item.precio.toFixed(2)} €</strong>
                    <button class="cart-item-delete" onclick="eliminarDelCarrito('${item.id}')">✖</button>
                `;
                lista.appendChild(li);
            });

            // Lógica de Descuentos por Cantidad (Opción 3)
            const cantidadCarteras = itemsCarrito.length;
            if (cantidadCarteras === 1) {
                descuentoPorcentaje = 0;
                descuentoValor = 0;
                promoBadgeContainer.innerHTML = `
                    <div class="promo-discount-badge promo-badge-info">
                        💡 ¡Añade otra cartera y consigue un 10% de DESCUENTO en todo!
                    </div>
                `;
                discountSummaryLine.style.display = 'none';
            } else if (cantidadCarteras === 2) {
                descuentoPorcentaje = 10;
                descuentoValor = subtotal * 0.10;
                promoBadgeContainer.innerHTML = `
                    <div class="promo-discount-badge promo-badge-success">
                        🎉 ¡10% de descuento aplicado! Añade 1 más para conseguir un 15%.
                    </div>
                `;
                discountSummaryLine.style.display = 'flex';
                discountValueText.innerText = descuentoValor.toFixed(2);
            } else if (cantidadCarteras >= 3) {
                descuentoPorcentaje = 15;
                descuentoValor = subtotal * 0.15;
                promoBadgeContainer.innerHTML = `
                    <div class="promo-discount-badge promo-badge-success">
                        🔥 ¡Máximo descuento del 15% aplicado a tu pedido!
                    </div>
                `;
                discountSummaryLine.style.display = 'flex';
                discountValueText.innerText = descuentoValor.toFixed(2);
            }

            // Subtotal después de aplicar el descuento correspondiente
            subtotalConDescuento = subtotal - descuentoValor;

            // Regla de envío: Gratis si el subtotal final es mayor o igual a 30 €
            if (subtotalConDescuento >= 30) {
                costeEnvio = 0;
                shippingText.innerText = "¡GRATIS!";
                shippingText.style.color = "#047857";
                shippingText.style.fontWeight = "bold";
                freeShippingAlert.innerHTML = "🎉 ¡Felicidades! Tienes envío gratis certificado";
                freeShippingAlert.style.backgroundColor = "#ecfdf5";
                freeShippingAlert.style.color = "#047857";
            } else {
                costeEnvio = 3.99;
                shippingText.innerText = "3.99 €";
                shippingText.style.color = "inherit";
                shippingText.style.fontWeight = "normal";
                let restante = (30 - subtotalConDescuento).toFixed(2);
                freeShippingAlert.innerHTML = `Faltan <strong>${restante} €</strong> para el envío GRATIS.`;
                freeShippingAlert.style.backgroundColor = "#fffbeb";
                freeShippingAlert.style.color = "#b45309";
            }

            total = subtotalConDescuento + costeEnvio;

            subtotalText.innerText = subtotal.toFixed(2);
            totalText.innerText = total.toFixed(2);
            cartCount.innerText = itemsCarrito.length;
        }

        // CONTROL DE MODAL DE CHECKOUT Y DATOS DE CLIENTE
        function finalizarCompra() {
            if (itemsCarrito.length === 0) {
                showToast("¡El carrito está vacío! Añade un producto antes de continuar.", "error");
                return;
            }

            // Actualizar resumen visual del checkout antes de abrir
            const listContainer = document.getElementById('checkout-items-list');
            listContainer.innerHTML = "";

            itemsCarrito.forEach(item => {
                const line = document.createElement('div');
                line.className = 'chk-item-line';
                line.innerHTML = `
                    <span>• <strong>${item.nombre}</strong> (${item.especificaciones})</span>
                    <strong>${item.precio.toFixed(2)}€</strong>
                `;
                listContainer.appendChild(line);
            });

            // Configurar los subtotales, descuentos y totales finales en el modal
            document.getElementById('checkout-subtotal-val').innerText = `${subtotal.toFixed(2)} €`;
            
            const checkoutDiscountRow = document.getElementById('checkout-discount-row');
            if (descuentoValor > 0) {
                checkoutDiscountRow.style.display = 'flex';
                document.getElementById('checkout-discount-val').innerText = `-${descuentoValor.toFixed(2)} € (${descuentoPorcentaje}%)`;
            } else {
                checkoutDiscountRow.style.display = 'none';
            }

            document.getElementById('checkout-shipping-val').innerText = costeEnvio === 0 ? "¡Gratis!" : `${costeEnvio.toFixed(2)} €`;
            document.getElementById('checkout-total-val').innerText = `${total.toFixed(2)} €`;

            // Ocultar carrito lateral y activar modal de pago
            document.getElementById('carrito-lateral').classList.remove('abierto');
            document.getElementById('checkout-modal-overlay').classList.add('activo');
        }

        function cerrarCheckout() {
            document.getElementById('checkout-modal-overlay').classList.remove('activo');
        }

        function selectPayment(metodo) {
            metodoPagoSeleccionado = metodo;
            
            document.getElementById('opt-bizum').classList.remove('selected');
            document.getElementById('opt-transfer').classList.remove('selected');

            const instructions = document.getElementById('payment-instructions');

            if (metodo === 'Bizum') {
                document.getElementById('opt-bizum').classList.add('selected');
                instructions.innerHTML = `Realizarás un <strong>Bizum rápido y seguro al 679 01 64 77</strong> tras confirmar el pedido. En el chat de WhatsApp te facilitaremos el concepto y coordinaremos las imágenes personalizadas.`;
            } else {
                document.getElementById('opt-transfer').classList.add('selected');
                instructions.innerHTML = `Te enviaremos los <strong>datos bancarios (IBAN)</strong> directamente por el chat de WhatsApp para que realices una transferencia segura por el total de tu pedido.`;
            }
        }

        // PROCESADO DE PEDIDO FINAL Y REDIRECCIÓN A WHATSAPP
        function procesarPedido(event) {
            event.preventDefault();

            // Capturar datos del cliente
            const nombre = document.getElementById('order-name').value;
            const direccion = document.getElementById('order-address').value;
            const telefono = document.getElementById('order-phone').value;

            // Formatear texto del pedido
            let textoProductos = "";
            itemsCarrito.forEach((item, index) => {
                textoProductos += `${index + 1}. *${item.nombre}*\n`;
                textoProductos += `   ↳ *Especificaciones:* _${item.especificaciones}_\n`;
                textoProductos += `   ↳ *Precio unitario:* ${item.precio.toFixed(2)}€\n\n`;
            });

            const envioTexto = costeEnvio === 0 ? "¡GRATIS!" : `${costeEnvio.toFixed(2)}€`;
            let descuentoTexto = descuentoValor > 0 ? `-${descuentoValor.toFixed(2)}€ (${descuentoPorcentaje}% descuento por volumen)` : "No aplicado";

            // Construir plantilla oficial de WhatsApp
            const mensajeOriginal = 
`🛍️ *¡NUEVO PEDIDO DE WALLMAN STORE!*
----------------------------------------
👤 *Cliente:* ${nombre}
📞 *Teléfono:* ${telefono}
📍 *Envío:* ${direccion}
💳 *Método de Pago:* ${metodoPagoSeleccionado}
----------------------------------------

📝 *RESUMEN DE PRODUCTOS:*
${textoProductos}
💰 *Subtotal Productos:* ${subtotal.toFixed(2)}€
🏷️ *Descuento:* ${descuentoTexto}
📦 *Envío:* ${envioTexto}
⭐ *TOTAL DEL PEDIDO:* *${total.toFixed(2)} €*

----------------------------------------
⚠️ *ADVERTENCIA DE PERSONALIZACIÓN PARA EL CLIENTE:*
_Por favor, adjunta justo después de este mensaje las imágenes, dibujos de líneas o fotos cargadas en la web utilizando el botón de clip 📎 o cámara 📷 en este chat de WhatsApp._`;

            // Codificar el mensaje
            const mensajeCodificado = encodeURIComponent(mensajeOriginal);
            
            // Link de llamada directa de WhatsApp API
            const urlWhatsApp = `https://api.whatsapp.com/send?phone=34679016477&text=${mensajeCodificado}`;

            // Abrir WhatsApp en pestaña nueva
            window.open(urlWhatsApp, '_blank');

            showToast("¡Redirigiendo a tu WhatsApp para finalizar el pedido!", "success");
            cerrarCheckout();

            // Limpiar carrito y LocalStorage tras completar el flujo de compra
            setTimeout(() => {
                itemsCarrito = [];
                localStorage.removeItem('wallman_cart');
                actualizarInterfazCarrito();
                document.getElementById('checkout-form').reset();
            }, 1000);
        }
    </script>

</body>
</html>
