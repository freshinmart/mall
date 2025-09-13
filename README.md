<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fresh.in - Belanja Kebutuhan Sehari-hari</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&family=Montserrat:wght@700;800;900&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #4CAF50;
            --primary-light: #E8F5E9;
            --accent: #FF9800;
            --secondary: #2196F3;
            --light: #FFFFFF;
            --dark: #263238;
            --gray-light: #F5F7FA;
            --gray: #78909C;
            --gray-dark: #546E7A;
            --success: #66BB6A;
            --warning: #FFA726;
            --error: #EF5350;
            --border-radius: 12px;
            --box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
            --transition: all 0.3s ease;
            --header-height: 70px;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background-color: var(--gray-light);
            color: var(--dark);
            overflow-x: hidden;
            line-height: 1.6;
            padding-top: var(--header-height);
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }

        /* Header Styles - Diperbaiki untuk mobile */
        header {
            background-color: rgba(255, 255, 255, 0.95);
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 1000;
            height: var(--header-height);
            transition: var(--transition);
        }

        .header-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            height: 100%;
            padding: 0 15px;
        }

        .header-left {
            display: flex;
            align-items: center;
        }

        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            font-size: 20px;
            color: var(--dark);
            cursor: pointer;
            margin-right: 15px;
        }

        .logo {
            display: flex;
            align-items: center;
        }

        .logo h1 {
            font-family: 'Montserrat', sans-serif;
            font-size: 22px;
            font-weight: 800;
            letter-spacing: -0.5px;
        }

        .fresh {
            color: var(--primary);
        }

        .dot-in {
            color: var(--accent);
        }

        .header-center {
            flex: 1;
            max-width: 500px;
            margin: 0 15px;
            position: relative;
        }

        .search-bar input {
            width: 100%;
            padding: 10px 15px;
            border: 1px solid #e0e0e0;
            border-radius: 24px;
            font-size: 14px;
            transition: var(--transition);
            background-color: var(--gray-light);
        }

        .search-bar input:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 2px rgba(76, 175, 80, 0.2);
        }

        .search-bar button {
            position: absolute;
            right: 4px;
            top: 4px;
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 20px;
            padding: 6px 12px;
            cursor: pointer;
            transition: var(--transition);
            font-weight: 500;
            font-size: 13px;
        }

        .header-right {
            display: flex;
            gap: 12px;
        }

        .icon-link {
            position: relative;
            color: var(--dark);
            font-size: 18px;
            text-decoration: none;
            transition: var(--transition);
            display: flex;
            align-items: center;
        }

        .icon-link:hover {
            color: var(--primary);
        }

        .icon-link .label {
            font-size: 14px;
            margin-left: 5px;
            display: none;
        }

        .cart-count, .wishlist-count {
            position: absolute;
            top: -8px;
            right: -8px;
            background: var(--primary);
            color: white;
            font-size: 11px;
            width: 18px;
            height: 18px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        /* Mobile Menu */
        .mobile-menu {
            position: fixed;
            top: var(--header-height);
            left: -100%;
            width: 80%;
            height: calc(100vh - var(--header-height));
            background: var(--light);
            z-index: 999;
            transition: var(--transition);
            overflow-y: auto;
            box-shadow: 2px 0 10px rgba(0, 0, 0, 0.1);
        }

        .mobile-menu.active {
            left: 0;
        }

        .mobile-menu-header {
            padding: 12px 15px;
            background: var(--primary);
            color: white;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .mobile-menu-close {
            background: none;
            border: none;
            color: white;
            font-size: 20px;
            cursor: pointer;
        }

        .mobile-menu-categories {
            padding: 15px;
        }

        .mobile-menu-category {
            margin-bottom: 15px;
        }

        .mobile-menu-category-title {
            font-weight: 600;
            margin-bottom: 10px;
            padding-bottom: 5px;
            border-bottom: 1px solid #eee;
            color: var(--primary);
        }

        .mobile-menu-links {
            list-style: none;
        }

        .mobile-menu-links li {
            margin-bottom: 8px;
        }

        .mobile-menu-links a {
            display: block;
            padding: 10px;
            color: var(--dark);
            text-decoration: none;
            border-radius: 6px;
            transition: var(--transition);
        }

        .mobile-menu-links a:hover {
            background: var(--primary-light);
            color: var(--primary);
        }

        .mobile-menu-links a i {
            margin-right: 10px;
            width: 20px;
            text-align: center;
        }

        /* Navigation Categories */
        .nav-categories {
            background: var(--light);
            padding: 10px 0;
            border-bottom: 1px solid #eee;
            overflow-x: auto;
            white-space: nowrap;
            scrollbar-width: none;
            -ms-overflow-style: none;
        }

        .nav-categories::-webkit-scrollbar {
            display: none;
        }

        .category-scroll {
            display: flex;
            gap: 10px;
            padding: 0 15px;
        }

        .category-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            text-decoration: none;
            color: var(--dark);
            min-width: 60px;
            transition: var(--transition);
            flex-shrink: 0;
        }

        .category-item:hover {
            color: var(--primary);
        }

        .category-icon {
            width: 36px;
            height: 36px;
            border-radius: 12px;
            background: var(--gray-light);
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 5px;
            font-size: 16px;
            color: var(--primary);
        }

        .category-name {
            font-size: 12px;
            text-align: center;
        }

        /* Hero Carousel */
        .hero-carousel {
            margin: 15px 0;
            border-radius: var(--border-radius);
            overflow: hidden;
            position: relative;
            height: 200px;
        }

        .carousel-container {
            position: relative;
            width: 100%;
            height: 100%;
            overflow: hidden;
        }

        .carousel-slides {
            display: flex;
            transition: transform 0.5s ease;
            height: 100%;
        }

        .carousel-slide {
            min-width: 100%;
            height: 100%;
            position: relative;
        }

        .carousel-slide img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            filter: brightness(0.9);
        }

        .carousel-content {
            position: absolute;
            bottom: 15px;
            left: 15px;
            color: white;
            z-index: 2;
            max-width: 70%;
        }

        .carousel-content h2 {
            font-size: 18px;
            font-weight: 700;
            margin-bottom: 8px;
        }

        .carousel-content p {
            font-size: 13px;
            opacity: 0.9;
            margin-bottom: 12px;
        }

        .hero-btn {
            display: inline-block;
            background: white;
            color: var(--primary);
            text-decoration: none;
            padding: 7px 14px;
            border-radius: 20px;
            font-weight: 600;
            font-size: 13px;
            transition: var(--transition);
            width: fit-content;
        }

        .carousel-controls {
            position: absolute;
            top: 50%;
            width: 100%;
            display: flex;
            justify-content: space-between;
            transform: translateY(-50%);
            z-index: 3;
            padding: 0 10px;
        }

        .carousel-control {
            background: rgba(0,0,0,0.5);
            color: white;
            border: none;
            padding: 8px;
            cursor: pointer;
            border-radius: 50%;
            width: 36px;
            height: 36px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 16px;
        }

        .carousel-dots {
            position: absolute;
            bottom: 10px;
            width: 100%;
            display: flex;
            justify-content: center;
            z-index: 3;
            gap: 8px;
        }

        .carousel-dot {
            width: 10px;
            height: 10px;
            border-radius: 50%;
            background: rgba(255,255,255,0.5);
            cursor: pointer;
            transition: var(--transition);
        }

        .carousel-dot.active {
            background: white;
            transform: scale(1.2);
        }

        /* Products Grid - Diperbaiki untuk responsivitas */
        .products-section {
            padding: 15px 0;
        }

        .section-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 12px;
        }

        .section-title {
            font-size: 17px;
            font-weight: 600;
            color: var(--dark);
        }

        .view-all {
            color: var(--primary);
            text-decoration: none;
            font-size: 14px;
            font-weight: 500;
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 12px;
        }

        @media (min-width: 480px) {
            .products-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }

        @media (min-width: 640px) {
            .products-grid {
                grid-template-columns: repeat(3, 1fr);
            }
        }

        @media (min-width: 768px) {
            .products-grid {
                grid-template-columns: repeat(4, 1fr);
            }
        }

        @media (min-width: 1024px) {
            .products-grid {
                grid-template-columns: repeat(5, 1fr);
            }
        }

        .product-card {
            background: var(--light);
            border-radius: var(--border-radius);
            overflow: hidden;
            box-shadow: var(--box-shadow);
            transition: var(--transition);
            position: relative;
        }

        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
        }

        .product-badge {
            position: absolute;
            top: 10px;
            left: 10px;
            background: var(--primary);
            color: white;
            padding: 3px 7px;
            border-radius: 4px;
            font-size: 10px;
            font-weight: 600;
            z-index: 2;
        }

        .product-image {
            height: 150px;
            width: 100%;
            background-color: var(--gray-light);
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            position: relative;
        }

        .product-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.3s;
        }

        .like-button {
            position: absolute;
            top: 10px;
            right: 10px;
            background: rgba(255, 255, 255, 0.9);
            border: none;
            border-radius: 50%;
            width: 30px;
            height: 30px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            z-index: 3;
            transition: var(--transition);
        }

        .like-button:hover {
            background: white;
            transform: scale(1.1);
        }

        .like-button i {
            color: #ccc;
            font-size: 15px;
            transition: var(--transition);
        }

        .like-button.liked i {
            color: var(--error);
        }

        .product-info {
            padding: 10px;
        }

        .product-title {
            font-size: 14px;
            font-weight: 500;
            margin-bottom: 5px;
            color: var(--dark);
            display: -webkit-box;
            -webkit-line-clamp: 2;
            -webkit-box-orient: vertical;
            overflow: hidden;
            height: 40px;
        }

        .product-price {
            display: flex;
            align-items: center;
            margin-bottom: 8px;
        }

        .current-price {
            font-size: 16px;
            font-weight: 700;
            color: var(--dark);
        }

        .original-price {
            font-size: 13px;
            color: var(--gray);
            text-decoration: line-through;
            margin-left: 8px;
        }

        .discount {
            background: var(--primary-light);
            color: var(--primary);
            font-size: 11px;
            font-weight: 600;
            padding: 2px 6px;
            border-radius: 4px;
            margin-left: 8px;
        }

        .add-to-cart {
            display: block;
            width: 100%;
            background: var(--primary);
            color: white;
            border: none;
            padding: 8px;
            border-radius: 6px;
            font-weight: 500;
            cursor: pointer;
            transition: var(--transition);
            font-size: 14px;
        }

        .add-to-cart:hover {
            background: #43A047;
        }

        /* Footer */
        footer {
            background: var(--light);
            padding: 25px 0 15px;
            margin-top: 30px;
        }

        .footer-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 25px;
        }

        @media (min-width: 640px) {
            .footer-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }

        @media (min-width: 768px) {
            .footer-grid {
                grid-template-columns: repeat(4, 1fr);
            }
        }

        .footer-logo {
            font-family: 'Montserrat', sans-serif;
            font-size: 20px;
            font-weight: 800;
            margin-bottom: 12px;
            display: block;
            text-decoration: none;
        }

        .footer-fresh {
            color: var(--primary);
        }

        .footer-in {
            color: var(--accent);
        }

        .footer-about p {
            color: var(--gray);
            margin-bottom: 15px;
            line-height: 1.7;
            font-size: 14px;
        }

        .social-links {
            display: flex;
            gap: 10px;
        }

        .social-links a {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 34px;
            height: 34px;
            background: var(--gray-light);
            color: var(--dark);
            border-radius: 50%;
            text-decoration: none;
            transition: var(--transition);
            font-size: 14px;
        }

        .social-links a:hover {
            background: var(--primary);
            color: white;
        }

        .footer-title {
            font-size: 16px;
            font-weight: 600;
            margin-bottom: 15px;
            color: var(--dark);
        }

        .footer-links {
            list-style: none;
        }

        .footer-links li {
            margin-bottom: 8px;
        }

        .footer-links a {
            color: var(--gray);
            text-decoration: none;
            transition: var(--transition);
            font-size: 14px;
        }

        .footer-links a:hover {
            color: var(--primary);
        }

        .copyright {
            text-align: center;
            padding-top: 15px;
            border-top: 1px solid #eee;
            color: var(--gray);
            font-size: 13px;
            margin-top: 15px;
        }

        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            z-index: 2000;
            align-items: center;
            justify-content: center;
            padding: 15px;
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background: white;
            border-radius: var(--border-radius);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
            width: 100%;
            max-width: 500px;
            overflow: hidden;
            animation: modalSlideUp 0.3s ease;
            max-height: 90vh;
            overflow-y: auto;
        }

        @keyframes modalSlideUp {
            from { transform: translateY(50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        .modal-header {
            padding: 15px 20px;
            border-bottom: 1px solid #eee;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            background: white;
            z-index: 10;
        }

        .modal-header h3 {
            font-size: 18px;
            font-weight: 600;
            color: var(--dark);
            flex: 1;
        }

        .modal-close {
            background: none;
            border: none;
            font-size: 24px;
            cursor: pointer;
            color: var(--gray);
        }

        .modal-body {
            padding: 15px 20px;
        }

        /* Cart Modal */
        .cart-item {
            display: flex;
            padding: 12px 0;
            border-bottom: 1px solid #eee;
        }

        .cart-item:last-child {
            border-bottom: none;
        }

        .cart-item-image {
            width: 70px;
            height: 70px;
            background: var(--gray-light);
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 12px;
            flex-shrink: 0;
        }

        .cart-item-image img {
            max-width: 80%;
            max-height: 80%;
            object-fit: cover;
        }

        .cart-item-details {
            flex: 1;
            min-width: 0;
        }

        .cart-item-title {
            font-weight: 500;
            margin-bottom: 5px;
            font-size: 14px;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        .cart-item-price {
            color: var(--dark);
            font-weight: 600;
            margin-bottom: 8px;
            font-size: 15px;
        }

        .cart-item-actions {
            display: flex;
            gap: 8px;
            align-items: center;
        }

        .quantity-control {
            display: flex;
            align-items: center;
            border: 1px solid #ddd;
            border-radius: 20px;
            overflow: hidden;
        }

        .quantity-btn {
            background: none;
            border: none;
            width: 28px;
            height: 28px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            font-size: 15px;
        }

        .quantity-input {
            width: 28px;
            text-align: center;
            border: none;
            background: transparent;
            font-size: 14px;
        }

        .remove-btn {
            background: none;
            border: none;
            color: var(--error);
            cursor: pointer;
            font-size: 12px;
            display: flex;
            align-items: center;
        }

        .remove-btn i {
            margin-right: 4px;
        }

        .cart-summary {
            padding: 12px 20px;
            border-top: 1px solid #eee;
            background: var(--gray-light);
            position: sticky;
            bottom: 0;
        }

        .summary-item {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
            font-size: 14px;
        }

        .summary-total {
            display: flex;
            justify-content: space-between;
            font-weight: 700;
            font-size: 16px;
            margin-top: 12px;
            padding-top: 12px;
            border-top: 1px solid #ddd;
        }

        .checkout-btn {
            display: block;
            width: 100%;
            background: var(--primary);
            color: white;
            border: none;
            padding: 10px;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
            font-size: 15px;
            text-align: center;
            text-decoration: none;
            margin-top: 12px;
        }

        .empty-cart {
            text-align: center;
            padding: 30px 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }

        .empty-cart i {
            font-size: 50px;
            color: #ddd;
            margin-bottom: 12px;
        }

        .empty-cart h4 {
            font-size: 17px;
            margin-bottom: 8px;
            color: var(--dark);
        }

        .empty-cart p {
            color: var(--gray);
            margin-bottom: 15px;
        }

        /* Checkout Modal */
        .checkout-steps {
            display: flex;
            justify-content: space-between;
            margin-bottom: 15px;
            position: relative;
        }

        .checkout-steps::before {
            content: '';
            position: absolute;
            top: 14px;
            left: 0;
            right: 0;
            height: 2px;
            background: #eee;
            z-index: 1;
        }

        .step {
            position: relative;
            z-index: 2;
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 25%;
        }

        .step-icon {
            width: 28px;
            height: 28px;
            border-radius: 50%;
            background: white;
            border: 2px solid #eee;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 13px;
            margin-bottom: 5px;
        }

        .step.active .step-icon {
            background: var(--primary);
            border-color: var(--primary);
            color: white;
        }

        .step.completed .step-icon {
            background: var(--success);
            border-color: var(--success);
            color: white;
        }

        .step-text {
            font-size: 11px;
            text-align: center;
            color: var(--gray);
        }

        .step.active .step-text {
            color: var(--primary);
            font-weight: 500;
        }

        .checkout-form {
            margin-top: 15px;
        }

        .form-group {
            margin-bottom: 12px;
        }

        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: 500;
            font-size: 14px;
        }

        .form-control {
            width: 100%;
            padding: 10px 15px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 14px;
            transition: var(--transition);
        }

        .form-control:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 2px rgba(76, 175, 80, 0.2);
        }

        .payment-options {
            margin-top: 15px;
        }

        .payment-option {
            display: flex;
            align-items: center;
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 8px;
            margin-bottom: 8px;
            cursor: pointer;
            transition: var(--transition);
        }

        .payment-option:hover {
            border-color: var(--primary);
        }

        .payment-option.selected {
            border-color: var(--primary);
            background-color: var(--primary-light);
        }

        .payment-option input {
            margin-right: 10px;
        }

        .payment-option-icon {
            margin-right: 8px;
            font-size: 18px;
            color: var(--primary);
        }

        .qris-preview {
            text-align: center;
            margin-top: 15px;
            padding: 12px;
            background: var(--gray-light);
            border-radius: 8px;
            display: none;
        }

        .qris-preview img {
            max-width: 180px;
            margin-bottom: 8px;
        }

        .payment-actions {
            display: flex;
            justify-content: space-between;
            margin-top: 15px;
            gap: 8px;
        }

        .btn {
            padding: 10px 18px;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
            border: none;
            flex: 1;
        }

        .btn-secondary {
            background: #e0e0e0;
            color: var(--dark);
        }

        .btn-primary {
            background: var(--primary);
            color: white;
        }

        .btn:disabled {
            opacity: 0.6;
            cursor: not-allowed;
        }

        /* QRIS Payment Verification */
        .payment-verification {
            margin-top: 15px;
            padding: 12px;
            background: var(--gray-light);
            border-radius: 8px;
            text-align: center;
        }

        .verification-status {
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 8px;
            font-size: 14px;
        }

        .verification-status i {
            font-size: 22px;
            margin-right: 8px;
        }

        .verification-status.verifying i {
            color: var(--warning);
            animation: spin 1s linear infinite;
        }

        .verification-status.success i {
            color: var(--success);
        }

        .verification-status.error i {
            color: var(--error);
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        /* Wishlist Page */
        .wishlist-page {
            display: none;
            padding: 20px 0;
        }

        .wishlist-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
        }

        @media (min-width: 640px) {
            .wishlist-grid {
                grid-template-columns: repeat(3, 1fr);
            }
        }

        @media (min-width: 768px) {
            .wishlist-grid {
                grid-template-columns: repeat(4, 1fr);
            }
        }

        /* Profile Page */
        .profile-page {
            display: none;
            padding: 20px 0;
        }

        .profile-card {
            background: white;
            border-radius: var(--border-radius);
            padding: 20px;
            box-shadow: var(--box-shadow);
        }

        /* Orders Page */
        .orders-page {
            display: none;
            padding: 20px 0;
        }

        .order-card {
            background: white;
            border-radius: var(--border-radius);
            padding: 15px;
            margin-bottom: 15px;
            box-shadow: var(--box-shadow);
        }

        /* History Page with Receipts */
        .history-page {
            display: none;
            padding: 20px 0;
        }

        .receipt-card {
            background: white;
            border-radius: var(--border-radius);
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: var(--box-shadow);
            position: relative;
        }

        .receipt-header {
            text-align: center;
            margin-bottom: 20px;
            border-bottom: 2px dashed #eee;
            padding-bottom: 15px;
        }

        .receipt-header h3 {
            font-family: 'Montserrat', sans-serif;
            color: var(--primary);
            margin-bottom: 5px;
            font-size: 22px;
        }

        .receipt-details {
            margin-bottom: 15px;
        }

        .receipt-item {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
            padding-bottom: 8px;
            border-bottom: 1px dashed #eee;
        }

        .receipt-total {
            display: flex;
            justify-content: space-between;
            font-weight: 700;
            margin-top: 15px;
            padding-top: 15px;
            border-top: 2px dashed #eee;
        }

        .receipt-footer {
            text-align: center;
            margin-top: 20px;
            color: var(--gray);
            font-size: 12px;
        }

        .print-receipt {
            position: absolute;
            top: 15px;
            right: 15px;
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
        }

        /* Admin Panel Styles */
        .admin-panel {
            display: none;
            padding: 20px 0;
        }

        .admin-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 1px solid #eee;
        }

        .admin-nav {
            background: white;
            border-radius: var(--border-radius);
            padding: 15px;
            margin-bottom: 20px;
            box-shadow: var(--box-shadow);
        }

        .admin-nav ul {
            display: flex;
            flex-wrap: wrap;
            list-style: none;
            gap: 10px;
        }

        .admin-nav a {
            display: block;
            padding: 10px 15px;
            background: var(--gray-light);
            color: var(--dark);
            text-decoration: none;
            border-radius: 6px;
            transition: var(--transition);
            font-weight: 500;
        }

        .admin-nav a:hover, .admin-nav a.active {
            background: var(--primary);
            color: white;
        }

        .admin-card {
            background: white;
            border-radius: var(--border-radius);
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: var(--box-shadow);
        }

        .admin-card-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 1px solid #eee;
        }

        .admin-card-title {
            font-size: 18px;
            font-weight: 600;
            color: var(--dark);
        }

        .admin-table {
            width: 100%;
            border-collapse: collapse;
        }

        .admin-table th, .admin-table td {
            padding: 12px 15px;
            text-align: left;
            border-bottom: 1px solid #eee;
        }

        .admin-table th {
            background: var(--gray-light);
            font-weight: 600;
        }

        .admin-table tr:hover {
            background: var(--primary-light);
        }

        .admin-action-btn {
            padding: 6px 12px;
            border-radius: 4px;
            border: none;
            cursor: pointer;
            font-size: 13px;
            margin-right: 5px;
            transition: var(--transition);
        }

        .btn-edit {
            background: var(--secondary);
            color: white;
        }

        .btn-delete {
            background: var(--error);
            color: white;
        }

        .btn-approve {
            background: var(--success);
            color: white;
        }

        .btn-reject {
            background: var(--warning);
            color: white;
        }

        .admin-form {
            display: grid;
            grid-template-columns: 1fr;
            gap: 15px;
        }

        @media (min-width: 768px) {
            .admin-form {
                grid-template-columns: 1fr 1fr;
            }
        }

        .admin-form .form-group.full-width {
            grid-column: 1 / -1;
        }

        .admin-stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin-bottom: 20px;
        }

        .stat-card {
            background: white;
            border-radius: var(--border-radius);
            padding: 20px;
            box-shadow: var(--box-shadow);
            text-align: center;
        }

        .stat-value {
            font-size: 24px;
            font-weight: 700;
            color: var(--primary);
            margin: 10px 0;
        }

        .stat-label {
            color: var(--gray);
            font-size: 14px;
        }

        .chart-container {
            height: 300px;
            margin-top: 20px;
        }

        /* Search Results Section */
        .search-results-section {
            display: none;
            padding: 20px 0;
        }
        
        .no-results {
            grid-column: 1 / -1;
            text-align: center;
            padding: 40px;
        }
        
        .no-results i {
            font-size: 48px;
            color: #ccc;
            margin-bottom: 16px;
        }
        
        /* Page container */
        .page {
            display: none;
        }
        
        .page.active {
            display: block;
        }
        
        /* Back button */
        .back-button {
            display: inline-flex;
            align-items: center;
            margin-bottom: 15px;
            color: var(--primary);
            text-decoration: none;
            font-weight: 500;
        }
        
        .back-button i {
            margin-right: 5px;
        }

        /* Admin Styles */
        .admin-btn {
            background: var(--primary);
            color: white;
            border: none;
            padding: 8px 15px;
            border-radius: 6px;
            cursor: pointer;
            font-weight: 500;
            transition: var(--transition);
        }
        
        .admin-btn:hover {
            background: #43A047;
        }

        /* Status badges */
        .status-badge {
            padding: 4px 8px;
            border-radius: 4px;
            font-size: 12px;
            font-weight: 500;
        }

        .status-badge.success {
            background: var(--primary-light);
            color: var(--success);
        }

        .status-badge.warning {
            background: #FFF3E0;
            color: var(--warning);
        }

        .status-badge.error {
            background: #FFEBEE;
            color: var(--error);
        }

        .status-badge.info {
            background: #E3F2FD;
            color: var(--secondary);
        }

        .status-badge.primary {
            background: #E8F5E9;
            color: var(--primary);
        }

        /* Responsive - Perbaikan khusus untuk tampilan mobile */
        @media (max-width: 768px) {
            :root {
                --header-height: 60px;
            }
            
            .header-container {
                padding: 0 10px;
            }
            
            .mobile-menu-btn {
                display: flex;
            }
            
            .header-center {
                margin: 0 10px;
                max-width: none;
            }
            
            .search-bar input {
                padding: 8px 15px;
                font-size: 14px;
            }
            
            .search-bar button {
                padding: 5px 12px;
                font-size: 12px;
            }
            
            .header-right {
                gap: 10px;
            }
            
            .icon-link {
                font-size: 16px;
            }
            
            .hero-carousel {
                height: 160px;
            }
            
            .carousel-content {
                bottom: 10px;
                left: 10px;
                max-width: 80%;
            }
            
            .carousel-content h2 {
                font-size: 16px;
            }
            
            .carousel-content p {
                font-size: 12px;
            }
            
            .products-grid, .wishlist-grid {
                grid-template-columns: repeat(2, 1fr);
                gap: 10px;
            }
            
            .product-image {
                height: 130px;
            }
            
            /* Header saat di-scroll */
            header.scrolled {
                box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            }
            
            /* Admin responsive */
            .admin-nav ul {
                flex-direction: column;
            }
            
            .admin-table {
                display: block;
                overflow-x: auto;
            }

            .modal-content {
                max-height: 85vh;
            }
        }

        @media (max-width: 480px) {
            :root {
                --header-height: 60px;
            }
            
            .logo h1 {
                font-size: 18px;
            }
            
            .search-bar input {
                padding: 6px 12px;
                font-size: 13px;
            }
            
            .search-bar button {
                padding: 4px 10px;
                font-size: 11px;
            }
            
            .icon-link {
                font-size: 15px;
            }
            
            .hero-carousel {
                height: 140px;
            }
            
            .carousel-content {
                padding: 10px;
            }
            
            .carousel-content h2 {
                font-size: 14px;
            }
            
            .carousel-content p {
                font-size: 11px;
                margin-bottom: 8px;
            }
            
            .hero-btn {
                padding: 5px 10px;
                font-size: 12px;
            }
            
            .products-grid, .wishlist-grid {
                grid-template-columns: 1fr;
            }
            
            .footer-grid {
                grid-template-columns: 1fr;
            }
            
            .admin-stats {
                grid-template-columns: 1fr;
            }

            .category-scroll {
                gap: 8px;
                padding: 0 10px;
            }

            .category-item {
                min-width: 50px;
            }

            .category-icon {
                width: 32px;
                height: 32px;
                font-size: 14px;
            }

            .category-name {
                font-size: 11px;
            }
        }

        @media (max-width: 360px) {
            .header-center {
                display: none;
            }

            .mobile-search-btn {
                display: block !important;
            }

            .products-grid, .wishlist-grid {
                grid-template-columns: 1fr;
            }

            .product-info {
                padding: 8px;
            }

            .product-title {
                font-size: 13px;
                height: 36px;
            }

            .current-price {
                font-size: 14px;
            }

            .add-to-cart {
                font-size: 12px;
                padding: 6px;
            }
        }

        /* Mobile search button */
        .mobile-search-btn {
            display: none;
            background: none;
            border: none;
            font-size: 18px;
            color: var(--dark);
            cursor: pointer;
        }

        /* Mobile search panel */
        .mobile-search-panel {
            display: none;
            position: fixed;
            top: var(--header-height);
            left: 0;
            width: 100%;
            background: white;
            padding: 15px;
            z-index: 999;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }

        .mobile-search-panel.active {
            display: block;
        }

        .mobile-search-container {
            display: flex;
            gap: 10px;
        }

        .mobile-search-input {
            flex: 1;
            padding: 10px 15px;
            border: 1px solid #e0e0e0;
            border-radius: 24px;
            font-size: 14px;
        }

        .mobile-search-close {
            background: none;
            border: none;
            font-size: 20px;
            color: var(--dark);
            cursor: pointer;
        }
    </style>
</head>
<body>
    <header id="main-header">
        <div class="header-container">
            <div class="header-left">
                <button class="mobile-menu-btn" id="mobile-menu-btn">
                    <i class="fas fa-bars"></i>
                </button>
                <div class="logo">
                    <h1><span class="fresh">Fresh</span><span class="dot-in">.in</span></h1>
                </div>
            </div>
            
            <div class="header-center">
                <div class="search-bar">
                    <input type="text" placeholder="Cari produk kebutuhan sehari-hari..." id="search-input">
                    <button id="search-btn"><i class="fas fa-search"></i> Cari</button>
                </div>
            </div>
            
            <div class="header-right">
                <button class="mobile-search-btn" id="mobile-search-btn">
                    <i class="fas fa-search"></i>
                </button>
                <a href="#" class="icon-link" id="wishlist-link">
                    <i class="far fa-heart"></i>
                    <span class="wishlist-count">0</span>
                </a>
                <a href="#" class="icon-link" id="cart-link">
                    <i class="fas fa-shopping-cart"></i>
                    <span class="cart-count">0</span>
                </a>
                <a href="#" class="icon-link" id="admin-link">
                    <i class="fas fa-cog"></i>
                </a>
            </div>
        </div>
    </header>

    <!-- Mobile Search Panel -->
    <div class="mobile-search-panel" id="mobile-search-panel">
        <div class="mobile-search-container">
            <input type="text" class="mobile-search-input" placeholder="Cari produk...">
            <button id="mobile-search-close" class="mobile-search-close">
                <i class="fas fa-times"></i>
            </button>
        </div>
    </div>

    <!-- Mobile Menu -->
    <div class="mobile-menu" id="mobile-menu">
        <div class="mobile-menu-header">
            <h3>Menu</h3>
            <button class="mobile-menu-close" id="mobile-menu-close">&times;</button>
        </div>
        <div class="mobile-menu-categories">
            <div class="mobile-menu-category">
                <h4 class="mobile-menu-category-title">Kategori</h4>
                <ul class="mobile-menu-links">
                    <li><a href="#" data-category="buah"><i class="fas fa-apple-alt"></i> Buah & Sayur</a></li>
                    <li><a href="#" data-category="minuman"><i class="fas fa-wine-bottle"></i> Minuman</a></li>
                    <li><a href="#" data-category="makanan"><i class="fas fa-bread-slice"></i> Makanan</a></li>
                    <li><a href="#" data-category="protein"><i class="fas fa-egg"></i> Protein</a></li>
                    <li><a href="#" data-category="kesehatan"><i class="fas fa-pump-medical"></i> Kesehatan</a></li>
                    <li><a href="#" data-category="rumahtangga"><i class="fas fa-home"></i> Rumah Tangga</a></li>
                </ul>
            </div>
            <div class="mobile-menu-category">
                <h4 class="mobile-menu-category-title">Akun Saya</h4>
                <ul class="mobile-menu-links">
                    <li><a href="#" data-page="profile"><i class="fas fa-user"></i> Profil</a></li>
                    <li><a href="#" data-page="orders"><i class="fas fa-shopping-bag"></i> Pesanan</a></li>
                    <li><a href="#" data-page="wishlist"><i class="fas fa-heart"></i> Wishlist</a></li>
                    <li><a href="#" data-page="history"><i class="fas fa-history"></i> Riwayat</a></li>
                </ul>
            </div>
            <div class="mobile-menu-category">
                <h4 class="mobile-menu-category-title">Lainnya</h4>
                <ul class="mobile-menu-links">
                    <li><a href="#" data-page="about"><i class="fas fa-info-circle"></i> Tentang Kami</a></li>
                    <li><a href="#" data-page="help"><i class="fas fa-headset"></i> Bantuan</a></li>
                    <li><a href="#" data-page="privacy"><i class="fas fa-shield-alt"></i> Kebijakan Privasi</a></li>
                    <li><a href="#" data-page="terms"><i class="fas fa-file-contract"></i> Syarat & Ketentuan</a></li>
                </ul>
            </div>
        </div>
    </div>

    <div class="nav-categories">
        <div class="category-scroll">
            <a href="#" class="category-item" data-category="buah">
                <div class="category-icon">
                    <i class="fas fa-apple-alt"></i>
                </div>
                <span class="category-name">Buah</span>
            </a>
            <a href="#" class="category-item" data-category="sayur">
                <div class="category-icon">
                    <i class="fas fa-carrot"></i>
                </div>
                <span class="category-name">Sayur</span>
            </a>
            <a href="#" class="category-item" data-category="protein">
                <div class="category-icon">
                    <i class="fas fa-egg"></i>
                </div>
                <span class="category-name">Protein</span>
            </a>
            <a href="#" class="category-item" data-category="minuman">
                <div class="category-icon">
                    <i class="fas fa-wine-bottle"></i>
                </div>
                <span class="category-name">Minuman</span>
            </a>
            <a href="#" class="category-item" data-category="roti">
                <div class="category-icon">
                    <i class="fas fa-bread-slice"></i>
                </div>
                <span class="category-name">Roti</span>
            </a>
            <a href="#" class="category-item" data-category="beku">
                <div class="category-icon">
                    <i class="fas fa-ice-cream"></i>
                </div>
                <span class="category-name">Beku</span>
            </a>
            <a href="#" class="category-item" data-category="snack">
                <div class="category-icon">
                    <i class="fas fa-pizza-slice"></i>
                </div>
                <span class="category-name">Snack</span>
            </a>
            <a href="#" class="category-item" data-category="kesehatan">
                <div class="category-icon">
                    <i class="fas fa-pump-medical"></i>
                </div>
                <span class="category-name">Kesehatan</span>
            </a>
        </div>
    </div>

    <!-- Home Page -->
    <div id="home-page" class="page active">
        <div class="container">
            <!-- Hero Carousel -->
            <div class="hero-carousel">
                <div class="carousel-container">
                    <div class="carousel-slides" id="carousel-slides">
                        <!-- Carousel slides will be populated by JavaScript -->
                    </div>
                    <div class="carousel-controls">
                        <button class="carousel-control prev" id="carousel-prev">&#10094;</button>
                        <button class="carousel-control next" id="carousel-next">&#10095;</button>
                    </div>
                    <div class="carousel-dots" id="carousel-dots">
                        <!-- Dots will be populated by JavaScript -->
                    </div>
                </div>
            </div>

            <!-- Search Results Section (Initially Hidden) -->
            <section class="search-results-section" id="search-results">
                <div class="section-header">
                    <h2 class="section-title">Hasil Pencarian</h2>
                    <button class="view-all" id="clear-search">Tutup Pencarian</button>
                </div>
                <div class="products-grid" id="search-results-grid">
                    <!-- Search results will be populated by JavaScript -->
                </div>
            </section>

            <section class="products-section" id="featured-section">
                <div class="section-header">
                    <h2 class="section-title">Produk Terlaris</h2>
                    <a href="#" class="view-all">Lihat Semua</a>
                </div>
                <div class="products-grid" id="featured-products">
                    <!-- Products will be populated by JavaScript -->
                </div>
            </section>

            <section class="products-section" id="promo-section">
                <div class="section-header">
                    <h2 class="section-title">Promo Spesial</h2>
                    <a href="#" class="view-all">Lihat Semua</a>
                </div>
                <div class="products-grid" id="promo-products">
                    <!-- Products will be populated by JavaScript -->
                </div>
            </section>

            <section class="products-section" id="all-products-section">
                <div class="section-header">
                    <h2 class="section-title">Semua Produk</h2>
                    <a href="#" class="view-all">Lihat Semua</a>
                </div>
                <div class="products-grid" id="all-products">
                    <!-- All products will be populated by JavaScript -->
                </div>
            </section>
        </div>
    </div>

    <!-- Wishlist Page -->
    <div id="wishlist-page" class="page">
        <div class="container">
            <a href="#" class="back-button" data-page="home">
                <i class="fas fa-arrow-left"></i> Kembali ke Beranda
            </a>
            <div class="section-header">
                <h2 class="section-title">Wishlist Saya</h2>
            </div>
            <div class="wishlist-grid" id="wishlist-products">
                <!-- Wishlist products will be populated by JavaScript -->
            </div>
        </div>
    </div>

    <!-- Profile Page -->
    <div id="profile-page" class="page">
        <div class="container">
            <a href="#" class="back-button" data-page="home">
                <i class="fas fa-arrow-left"></i> Kembali ke Beranda
            </a>
            <div class="section-header">
                <h2 class="section-title">Profil Saya</h2>
            </div>
            <div class="profile-card">
                <p>Halaman profil sedang dalam pengembangan. Fitur ini akan segera hadir!</p>
            </div>
        </div>
    </div>

    <!-- Orders Page -->
    <div id="orders-page" class="page">
        <div class="container">
            <a href="#" class="back-button" data-page="home">
                <i class="fas fa-arrow-left"></i> Kembali ke Beranda
            </a>
            <div class="section-header">
                <h2 class="section-title">Pesanan Saya</h2>
            </div>
            <div class="order-card">
                <p>Halaman pesanan sedang dalam pengembangan. Fitur ini akan segera hadir!</p>
            </div>
        </div>
    </div>

    <!-- History Page with Receipts -->
    <div id="history-page" class="page">
        <div class="container">
            <a href="#" class="back-button" data-page="home">
                <i class="fas fa-arrow-left"></i> Kembali ke Beranda
            </a>
            <div class="section-header">
                <h2 class="section-title">Riwayat Transaksi</h2>
            </div>
            <div id="history-receipts">
                <!-- Receipts will be populated by JavaScript -->
            </div>
        </div>
    </div>

    <!-- About Page -->
    <div id="about-page" class="page">
        <div class="container">
            <a href="#" class="back-button" data-page="home">
                <i class="fas fa-arrow-left"></i> Kembali ke Beranda
            </a>
            <div class="section-header">
                <h2 class="section-title">Tentang Kami</h2>
            </div>
            <div class="profile-card">
                <p>Fresh.in adalah platform belanja online kebutuhan sehari-hari dengan harga terbaik. Pengiriman cepat dan gratis.</p>
            </div>
        </div>
    </div>

    <!-- Help Page -->
    <div id="help-page" class="page">
        <div class="container">
            <a href="#" class="back-button" data-page="home">
                <i class="fas fa-arrow-left"></i> Kembali ke Beranda
            </a>
            <div class="section-header">
                <h2 class="section-title">Bantuan</h2>
            </div>
            <div class="profile-card">
                <p>Halaman bantuan sedang dalam pengembangan. Fitur ini akan segera hadir!</p>
            </div>
        </div>
    </div>

    <!-- Privacy Page -->
    <div id="privacy-page" class="page">
        <div class="container">
            <a href="#" class="back-button" data-page="home">
                <i class="fas fa-arrow-left"></i> Kembali ke Beranda
            </a>
            <div class="section-header">
                <h2 class="section-title">Kebijakan Privasi</h2>
            </div>
            <div class="profile-card">
                <p>Halaman kebijakan privasi sedang dalam pengembangan. Fitur ini akan segera hadir!</p>
            </div>
        </div>
    </div>

    <!-- Terms Page -->
    <div id="terms-page" class="page">
        <div class="container">
            <a href="#" class="back-button" data-page="home">
                <i class="fas fa-arrow-left"></i> Kembali ke Beranda
            </a>
            <div class="section-header">
                <h2 class="section-title">Syarat & Ketentuan</h2>
            </div>
            <div class="profile-card">
                <p>Halaman syarat dan ketentuan sedang dalam pengembangan. Fitur ini akan segera hadir!</p>
            </div>
        </div>
    </div>

    <!-- Admin Panel -->
    <div id="admin-page" class="page">
        <div class="container">
            <a href="#" class="back-button" data-page="home">
                <i class="fas fa-arrow-left"></i> Kembali ke Beranda
            </a>
            
            <div class="admin-header">
                <h2 class="section-title">Panel Admin</h2>
                <button class="admin-btn" id="admin-logout">
                    <i class="fas fa-sign-out-alt"></i> Logout
                </button>
            </div>
            
            <nav class="admin-nav">
                <ul>
                    <li><a href="#" class="admin-nav-link active" data-admin-section="dashboard">Dashboard</a></li>
                    <li><a href="#" class="admin-nav-link" data-admin-section="products">Manajemen Produk</a></li>
                    <li><a href="#" class="admin-nav-link" data-admin-section="orders">Manajemen Pesanan</a></li>
                    <li><a href="#" class="admin-nav-link" data-admin-section="users">Manajemen Pengguna</a></li>
                    <li><a href="#" class="admin-nav-link" data-admin-section="content">Manajemen Konten</a></li>
                    <li><a href="#" class="admin-nav-link" data-admin-section="reports">Laporan & Analitik</a></li>
                </ul>
            </nav>
            
            <!-- Admin Dashboard -->
            <div id="admin-dashboard" class="admin-section active">
                <div class="admin-stats">
                    <div class="stat-card">
                        <i class="fas fa-shopping-cart fa-2x"></i>
                        <div class="stat-value" id="total-orders">0</div>
                        <div class="stat-label">Total Pesanan</div>
                    </div>
                    <div class="stat-card">
                        <i class="fas fa-box fa-2x"></i>
                        <div class="stat-value" id="total-products">0</div>
                        <div class="stat-label">Total Produk</div>
                    </div>
                    <div class="stat-card">
                        <i class="fas fa-users fa-2x"></i>
                        <div class="stat-value" id="total-users">0</div>
                        <div class="stat-label">Total Pengguna</div>
                    </div>
                    <div class="stat-card">
                        <i class="fas fa-money-bill-wave fa-2x"></i>
                        <div class="stat-value" id="total-revenue">Rp 0</div>
                        <div class="stat-label">Total Pendapatan</div>
                    </div>
                </div>
                
                <div class="admin-card">
                    <div class="admin-card-header">
                        <h3 class="admin-card-title">Pesanan Terbaru</h3>
                    </div>
                    <div class="table-responsive">
                        <table class="admin-table">
                            <thead>
                                <tr>
                                    <th>ID Pesanan</th>
                                    <th>Pelanggan</th>
                                    <th>Tanggal</th>
                                    <th>Total</th>
                                    <th>Status</th>
                                    <th>Aksi</th>
                                </tr>
                            </thead>
                            <tbody id="recent-orders-table">
                                <!-- Recent orders will be populated by JavaScript -->
                            </tbody>
                        </table>
                    </div>
                </div>
                
                <div class="admin-card">
                    <div class="admin-card-header">
                        <h3 class="admin-card-title">Produk Perlu Persetujuan</h3>
                    </div>
                    <div class="table-responsive">
                        <table class="admin-table">
                            <thead>
                                <tr>
                                    <th>Nama Produk</th>
                                    <th>Penjual</th>
                                    <th>Harga</th>
                                    <th>Tanggal</th>
                                    <th>Aksi</th>
                                </tr>
                            </thead>
                            <tbody id="pending-products-table">
                                <!-- Pending products will be populated by JavaScript -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
            
            <!-- Admin Products Management -->
            <div id="admin-products" class="admin-section">
                <div class="admin-card">
                    <div class="admin-card-header">
                        <h3 class="admin-card-title">Daftar Produk</h3>
                        <button class="admin-btn" id="add-product-btn">
                            <i class="fas fa-plus"></i> Tambah Produk
                        </button>
                    </div>
                    <div class="table-responsive">
                        <table class="admin-table">
                            <thead>
                                <tr>
                                    <th>Nama</th>
                                    <th>Kategori</th>
                                    <th>Harga</th>
                                    <th>Stok</th>
                                    <th>Status</th>
                                    <th>Aksi</th>
                                </tr>
                            </thead>
                            <tbody id="products-table">
                                <!-- Products will be populated by JavaScript -->
                            </tbody>
                        </table>
                    </div>
                </div>
                
                <!-- Add/Edit Product Form (Initially Hidden) -->
                <div class="admin-card" id="product-form-container" style="display: none;">
                    <div class="admin-card-header">
                        <h3 class="admin-card-title" id="product-form-title">Tambah Produk Baru</h3>
                        <button class="btn btn-secondary" id="cancel-product-form">
                            <i class="fas fa-times"></i> Batal
                        </button>
                    </div>
                    <div class="admin-form">
                        <div class="form-group">
                            <label for="product-name">Nama Produk</label>
                            <input type="text" id="product-name" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="product-category">Kategori</label>
                            <select id="product-category" class="form-control" required>
                                <option value="">Pilih Kategori</option>
                                <option value="buah">Buah</option>
                                <option value="sayur">Sayur</option>
                                <option value="protein">Protein</option>
                                <option value="minuman">Minuman</option>
                                <option value="roti">Roti</option>
                                <option value="beku">Beku</option>
                                <option value="snack">Snack</option>
                                <option value="kesehatan">Kesehatan</option>
                                <option value="rumahtangga">Rumah Tangga</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label for="product-price">Harga (Rp)</label>
                            <input type="number" id="product-price" class="form-control" min="0" required>
                        </div>
                        <div class="form-group">
                            <label for="product-original-price">Harga Asli (Rp) - Opsional</label>
                            <input type="number" id="product-original-price" class="form-control" min="0">
                        </div>
                        <div class="form-group">
                            <label for="product-stock">Stok</label>
                            <input type="number" id="product-stock" class="form-control" min="0" required>
                        </div>
                        <div class="form-group full-width">
                            <label for="product-image">URL Gambar</label>
                            <input type="text" id="product-image" class="form-control" placeholder="https://example.com/image.jpg">
                        </div>
                        <div class="form-group full-width">
                            <label for="product-description">Deskripsi</label>
                            <textarea id="product-description" class="form-control" rows="3"></textarea>
                        </div>
                        <div class="form-group full-width">
                            <button class="btn btn-primary" id="save-product">
                                <i class="fas fa-save"></i> Simpan Produk
                            </button>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Admin Orders Management -->
            <div id="admin-orders" class="admin-section">
                <div class="admin-card">
                    <div class="admin-card-header">
                        <h3 class="admin-card-title">Manajemen Pesanan</h3>
                    </div>
                    <div class="table-responsive">
                        <table class="admin-table">
                            <thead>
                                <tr>
                                    <th>ID Pesanan</th>
                                    <th>Pelanggan</th>
                                    <th>Tanggal</th>
                                    <th>Items</th>
                                    <th>Total</th>
                                    <th>Status</th>
                                    <th>Aksi</th>
                                </tr>
                            </thead>
                            <tbody id="orders-table">
                                <!-- Orders will be populated by JavaScript -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
            
            <!-- Admin Users Management -->
            <div id="admin-users" class="admin-section">
                <div class="admin-card">
                    <div class="admin-card-header">
                        <h3 class="admin-card-title">Manajemen Pengguna</h3>
                    </div>
                    <div class="table-responsive">
                        <table class="admin-table">
                            <thead>
                                <tr>
                                    <th>Nama</th>
                                    <th>Email</th>
                                    <th>Peran</th>
                                    <th>Tanggal Daftar</th>
                                    <th>Status</th>
                                    <th>Aksi</th>
                                </tr>
                            </thead>
                            <tbody id="users-table">
                                <!-- Users will be populated by JavaScript -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
            
            <!-- Admin Content Management -->
            <div id="admin-content" class="admin-section">
                <div class="admin-card">
                    <div class="admin-card-header">
                        <h3 class="admin-card-title">Kelola Banner Promosi</h3>
                        <button class="admin-btn" id="add-banner-btn">
                            <i class="fas fa-plus"></i> Tambah Banner
                        </button>
                    </div>
                    <div class="table-responsive">
                        <table class="admin-table">
                            <thead>
                                <tr>
                                    <th>Gambar</th>
                                    <th>Judul</th>
                                    <th>Deskripsi</th>
                                    <th>Status</th>
                                    <th>Aksi</th>
                                </tr>
                            </thead>
                            <tbody id="banners-table">
                                <!-- Banners will be populated by JavaScript -->
                            </tbody>
                        </table>
                    </div>
                </div>
                
                <!-- Banner Form (Initially Hidden) -->
                <div class="admin-card" id="banner-form-container" style="display: none;">
                    <div class="admin-card-header">
                        <h3 class="admin-card-title" id="banner-form-title">Tambah Banner Baru</h3>
                        <button class="btn btn-secondary" id="cancel-banner-form">
                            <i class="fas fa-times"></i> Batal
                        </button>
                    </div>
                    <div class="admin-form">
                        <div class="form-group">
                            <label for="banner-title">Judul Banner</label>
                            <input type="text" id="banner-title" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="banner-description">Deskripsi</label>
                            <textarea id="banner-description" class="form-control" rows="2" required></textarea>
                        </div>
                        <div class="form-group">
                            <label for="banner-image">URL Gambar</label>
                            <input type="text" id="banner-image" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="banner-status">Status</label>
                            <select id="banner-status" class="form-control" required>
                                <option value="active">Aktif</option>
                                <option value="inactive">Nonaktif</option>
                            </select>
                        </div>
                        <div class="form-group full-width">
                            <button class="btn btn-primary" id="save-banner">
                                <i class="fas fa-save"></i> Simpan Banner
                            </button>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Admin Reports & Analytics -->
            <div id="admin-reports" class="admin-section">
                <div class="admin-card">
                    <div class="admin-card-header">
                        <h3 class="admin-card-title">Laporan Penjualan</h3>
                        <div>
                            <select id="report-period" class="form-control" style="display: inline-block; width: auto;">
                                <option value="7">7 Hari Terakhir</option>
                                <option value="30" selected>30 Hari Terakhir</option>
                                <option value="90">3 Bulan Terakhir</option>
                                <option value="365">Tahun Ini</option>
                            </select>
                        </div>
                    </div>
                    <div class="chart-container">
                        <canvas id="sales-chart"></canvas>
                    </div>
                </div>
                
                <div class="admin-card">
                    <div class="admin-card-header">
                        <h3 class="admin-card-title">Produk Terlaris</h3>
                    </div>
                    <div class="table-responsive">
                        <table class="admin-table">
                            <thead>
                                <tr>
                                    <th>Produk</th>
                                    <th>Terjual</th>
                                    <th>Pendapatan</th>
                                    <th>Rating</th>
                                </tr>
                            </thead>
                            <tbody id="best-selling-products">
                                <!-- Best selling products will be populated by JavaScript -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <footer>
        <div class="container">
            <div class="footer-grid">
                <div class="footer-about">
                    <a href="#" class="footer-logo"><span class="footer-fresh">Fresh</span><span class="footer-in">.in</span></a>
                    <p>Platform belanja online kebutuhan sehari-hari dengan harga terbaik. Pengiriman cepat dan gratis.</p>
                    <div class="social-links">
                        <a href="#"><i class="fab fa-facebook-f"></i></a>
                        <a href="#"><i class="fab fa-instagram"></i></a>
                        <a href="#"><i class="fab fa-twitter"></i></a>
                    </div>
                </div>
                <div class="footer-links-container">
                    <h3 class="footer-title">Layanan</h3>
                    <ul class="footer-links">
                        <li><a href="#" data-page="help">Bantuan</a></li>
                        <li><a href="#">Metode Pembayaran</a></li>
                        <li><a href="#">Pengiriman</a></li>
                        <li><a href="#">Pengembalian</a></li>
                    </ul>
                </div>
                <div class="footer-links-container">
                    <h3 class="footer-title">Tentang Kami</h3>
                    <ul class="footer-links">
                        <li><a href="#" data-page="about">Tentang Fresh.in</a></li>
                        <li><a href="#">Karir</a></li>
                        <li><a href="#" data-page="privacy">Kebijakan Privasi</a></li>
                        <li><a href="#" data-page="terms">Syarat & Ketentuan</a></li>
                    </ul>
                </div>
                <div class="footer-contact">
                    <h3 class="footer-title">Hubungi Kami</h3>
                    <ul class="footer-links">
                        <li><i class="fas fa-phone"></i> (021) 1234-5678</li>
                        <li><i class="fas fa-envelope"></i> cs@fresh.in</li>
                        <li><i class="fas fa-map-marker-alt"></i> Jakarta, Indonesia</li>
                    </ul>
                </div>
            </div>
            <div class="copyright">
                <p>&copy; 2023 Fresh.in. All rights reserved.</p>
            </div>
        </div>
    </footer>

    <!-- Cart Modal -->
    <div class="modal" id="cart-modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3>Keranjang Belanja</h3>
                <button class="modal-close" id="close-cart">&times;</button>
            </div>
            <div class="modal-body" id="cart-body">
                <!-- Cart items will be populated by JavaScript -->
            </div>
        </div>
    </div>

    <!-- Checkout Modal -->
    <div class="modal" id="checkout-modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3>Checkout</h3>
                <button class="modal-close" id="close-checkout">&times;</button>
            </div>
            <div class="modal-body">
                <div class="checkout-steps">
                    <div class="step active" id="step-1">
                        <div class="step-icon">1</div>
                        <div class="step-text">Informasi</div>
                    </div>
                    <div class="step" id="step-2">
                        <div class="step-icon">2</div>
                        <div class="step-text">Pembayaran</div>
                    </div>
                    <div class="step" id="step-3">
                        <div class="step-icon">3</div>
                        <div class="step-text">Konfirmasi</div>
                    </div>
                </div>

                <div class="checkout-form">
                    <!-- Step 1: Customer Information -->
                    <div id="checkout-step-1">
                        <div class="form-group">
                            <label for="customer-name">Nama Lengkap</label>
                            <input type="text" id="customer-name" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="customer-email">Email</label>
                            <input type="email" id="customer-email" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="customer-phone">Nomor Telepon</label>
                            <input type="tel" id="customer-phone" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="customer-address">Alamat Lengkap</label>
                            <textarea id="customer-address" class="form-control" rows="3" required></textarea>
                        </div>
                        <div class="payment-actions">
                            <button class="btn btn-secondary" id="cancel-checkout">Batal</button>
                            <button class="btn btn-primary" id="next-to-payment">Lanjut</button>
                        </div>
                    </div>

                    <!-- Step 2: Payment Method -->
                    <div id="checkout-step-2" style="display: none;">
                        <div class="payment-options">
                            <div class="payment-option selected" data-method="qris">
                                <input type="radio" name="payment-method" id="payment-qris" checked>
                                <div class="payment-option-icon">
                                    <i class="fas fa-qrcode"></i>
                                </div>
                                <label for="payment-qris">QRIS</label>
                            </div>
                            <div class="payment-option" data-method="cod">
                                <input type="radio" name="payment-method" id="payment-cod">
                                <div class="payment-option-icon">
                                    <i class="fas fa-money-bill-wave"></i>
                                </div>
                                <label for="payment-cod">Cash on Delivery</label>
                            </div>
                        </div>

                        <div class="qris-preview" id="qris-preview">
                            <img src="" alt="QR Code" id="qris-image">
                            <p>Scan QR code di atas untuk melakukan pembayaran</p>
                        </div>

                        <div class="payment-verification" id="payment-verification" style="display: none;">
                            <div class="verification-status verifying">
                                <i class="fas fa-spinner"></i>
                                <span>Memverifikasi pembayaran...</span>
                            </div>
                            <p>Silakan selesaikan pembayaran Anda melalui aplikasi e-wallet atau mobile banking</p>
                        </div>

                        <div class="payment-actions">
                            <button class="btn btn-secondary" id="back-to-info">Kembali</button>
                            <button class="btn btn-primary" id="next-to-confirm">Lanjut</button>
                        </div>
                    </div>

                    <!-- Step 3: Confirmation -->
                    <div id="checkout-step-3" style="display: none;">
                        <div id="order-summary">
                            <!-- Order summary will be populated by JavaScript -->
                        </div>
                        <div class="payment-actions">
                            <button class="btn btn-secondary" id="back-to-payment">Kembali</button>
                            <button class="btn btn-primary" id="confirm-order">Konfirmasi Pesanan</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Admin Login Modal -->
    <div class="modal" id="admin-login-modal">
        <div class="modal-content" style="max-width: 400px;">
            <div class="modal-header">
                <h3>Admin Login</h3>
                <button class="modal-close" id="close-admin-login">&times;</button>
            </div>
            <div class="modal-body">
                <div class="form-group">
                    <label for="admin-username">Username</label>
                    <input type="text" id="admin-username" class="form-control" placeholder="Masukkan username">
                </div>
                <div class="form-group">
                    <label for="admin-password">Password</label>
                    <input type="password" id="admin-password" class="form-control" placeholder="Masukkan password">
                </div>
                <button class="btn btn-primary" id="admin-login-btn" style="width: 100%; margin-top: 15px;">Login</button>
            </div>
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <script>
        // =============================================
        // DATA MANAGEMENT - LOCALSTORAGE AS DATABASE
        // =============================================

        // Keys for localStorage
        const STORAGE_KEYS = {
            PRODUCTS: 'freshin_products',
            CAROUSEL: 'freshin_carousel',
            ORDERS: 'freshin_orders',
            USERS: 'freshin_users',
            BANNERS: 'freshin_banners',
            PENDING_PRODUCTS: 'freshin_pending_products',
            CART: 'freshin_cart',
            WISHLIST: 'freshin_wishlist'
        };

        // Default product data
        const DEFAULT_PRODUCTS = [
            { id: 1, name: "ALBA PASTILES 100 GR", price: 10500, category: "snack", image: "https://via.placeholder.com/200x200/FF5733/FFFFFF?text=ALBA", stock: 50 },
            { id: 2, name: "ALPENLIEBE SAC KARAMEL", price: 6750, category: "snack", image: "https://via.placeholder.com/200x200/FF5733/FFFFFF?text=ALPENLIEBE", stock: 45 },
            { id: 3, name: "ANLENE VANILA SCH 20 GR", price: 76500, category: "kesehatan", image: "https://via.placeholder.com/200x200/4FC3F7/FFFFFF?text=ANLENE", stock: 30 },
            { id: 4, name: "ANLENE ACTIFIT 590 GR", price: 76500, category: "kesehatan", image: "https://via.placeholder.com/200x200/4FC3F7/FFFFFF?text=ANLENE+ACTIFIT", stock: 25 },
            { id: 5, name: "AQUA 600 ML", price: 3000, category: "minuman", image: "https://via.placeholder.com/200x200/4FC3F7/FFFFFF?text=AQUA", stock: 100 },
            { id: 6, name: "AQUA ISI ULANG GALON", price: 19000, category: "minuman", image: "https://via.placeholder.com/200x200/4FC3F7/FFFFFF?text=AQUA+GALON", stock: 40 },
            { id: 7, name: "ATTACK 750 GR SOFTENER", price: 26575, category: "rumahtangga", image: "https://via.placeholder.com/200x200/4FC3F7/FFFFFF?text=ATTACK", stock: 20 },
            { id: 8, name: "ATTACK JAZZ 800 GR", price: 18490, category: "rumahtangga", image: "https://via.placeholder.com/200x200/4FC3F7/FFFFFF?text=JAZZ", stock: 15 },
            { id: 9, name: "ATTACK SOFT 70 GR 1x6", price: 11000, category: "rumahtangga", image: "https://via.placeholder.com/200x200/4FC3F7/FFFFFF?text=ATTACK+SOFT", stock: 35 },
            { id: 10, name: "ATTACK SOFTENER 450 GR", price: 14000, category: "rumahtangga", image: "https://via.placeholder.com/200x200/4FC3F7/FFFFFF?text=SOFTENER", stock: 28 },
            { id: 11, name: "BAHAN SIRUP MELON", price: 6500, category: "minuman", image: "https://via.placeholder.com/200x200/4FC3F7/FFFFFF?text=MELON", stock: 60 },
            { id: 12, name: "BENDERA Krimer Putih 6 sachet", price: 9000, category: "makanan", image: "https://via.placeholder.com/200x200/4FC3F7/FFFFFF?text=BENDERA+PUTIH", stock: 40 },
            { id: 13, name: "BENDERA Coklat 6 sachet", price: 9000, category: "makanan", image: "https://via.placeholder.com/200x200/4FC3F7/FFFFFF?text=BENDERA+COKLAT", stock: 40 },
            { id: 14, name: "BENG BENG 22 GR COKLAT", price: 2000, category: "snack", image: "https://via.placeholder.com/200x200/FF5733/FFFFFF?text=BENG+BENG", stock: 75, originalPrice: 2500, badge: "Sale" }
        ];

        // Default carousel data
        const DEFAULT_CAROUSEL_ITEMS = [
            { 
                id: 1, 
                image: "https://images.unsplash.com/photo-1542838132-92c53300491e?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80",
                title: "Belanja Lebih Mudah & Cepat",
                description: "Gratis ongkir untuk pembelian di atas Rp100.000"
            },
            { 
                id: 2, 
                image: "https://images.unsplash.com/photo-1565299624946-b28f40a0ae38?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80",
                title: "Produk Segar Setiap Hari",
                description: "Dikirim langsung dari petani terpercaya"
            },
            { 
                id: 3, 
                image: "https://images.unsplash.com/photo-1565958011703-44f9829ba187?ixlib=rb-1.2.1&auto=format&fit=crop&w=800&q=80",
                title: "Diskon Spesial Akhir Tahun",
                description: "Dapatkan penawaran terbatas untuk produk pilihan"
            }
        ];

        // Default admin data
        const DEFAULT_ADMIN_DATA = {
            orders: [],
            users: [
                { id: 1, name: "Admin User", email: "admin@fresh.in", role: "admin", joinDate: "01/01/2023", status: "active" }
            ],
            banners: [],
            pendingProducts: []
        };

        // Admin credentials
        const ADMIN_CREDENTIALS = {
            username: "admin",
            password: "admin123"
        };

        // App state
        let cart = [];
        let wishlist = [];
        let currentCheckoutStep = 1;
        let orderData = {};
        let currentPage = 'home';
        let lastScrollTop = 0;
        let isAdmin = false;
        let currentCarouselIndex = 0;
        let carouselInterval;
        let currentEditingProductId = null;
        let currentEditingBannerId = null;
        let salesChart = null;

        // Data from localStorage
        let products = [];
        let carouselItems = [];
        let adminData = {};

        // DOM Elements
        const cartCountElement = document.querySelector('.cart-count');
        const wishlistCountElement = document.querySelector('.wishlist-count');
        const cartBody = document.getElementById('cart-body');
        const featuredProductsGrid = document.getElementById('featured-products');
        const promoProductsGrid = document.getElementById('promo-products');
        const allProductsGrid = document.getElementById('all-products');
        const searchResultsGrid = document.getElementById('search-results-grid');
        const searchResultsSection = document.getElementById('search-results');
        const wishlistGrid = document.getElementById('wishlist-products');
        const cartModal = document.getElementById('cart-modal');
        const checkoutModal = document.getElementById('checkout-modal');
        const closeCartBtn = document.getElementById('close-cart');
        const closeCheckoutBtn = document.getElementById('close-checkout');
        const cartLink = document.getElementById('cart-link');
        const wishlistLink = document.getElementById('wishlist-link');
        const mobileMenuBtn = document.getElementById('mobile-menu-btn');
        const mobileMenu = document.getElementById('mobile-menu');
        const mobileMenuClose = document.getElementById('mobile-menu-close');
        const searchInput = document.getElementById('search-input');
        const searchBtn = document.getElementById('search-btn');
        const header = document.getElementById('main-header');
        const pages = document.querySelectorAll('.page');
        const adminLink = document.getElementById('admin-link');
        const adminLoginModal = document.getElementById('admin-login-modal');
        const closeAdminLogin = document.getElementById('close-admin-login');
        const adminLoginBtn = document.getElementById('admin-login-btn');
        const adminUsername = document.getElementById('admin-username');
        const adminPassword = document.getElementById('admin-password');
        const carouselSlides = document.getElementById('carousel-slides');
        const carouselDots = document.getElementById('carousel-dots');
        const carouselPrev = document.getElementById('carousel-prev');
        const carouselNext = document.getElementById('carousel-next');
        const historyReceipts = document.getElementById('history-receipts');
        const adminLogoutBtn = document.getElementById('admin-logout');
        const adminNavLinks = document.querySelectorAll('.admin-nav-link');
        const adminSections = document.querySelectorAll('.admin-section');
        const addProductBtn = document.getElementById('add-product-btn');
        const productFormContainer = document.getElementById('product-form-container');
        const productFormTitle = document.getElementById('product-form-title');
        const cancelProductForm = document.getElementById('cancel-product-form');
        const saveProductBtn = document.getElementById('save-product');
        const addBannerBtn = document.getElementById('add-banner-btn');
        const bannerFormContainer = document.getElementById('banner-form-container');
        const bannerFormTitle = document.getElementById('banner-form-title');
        const cancelBannerForm = document.getElementById('cancel-banner-form');
        const saveBannerBtn = document.getElementById('save-banner');
        const reportPeriod = document.getElementById('report-period');
        const mobileSearchBtn = document.getElementById('mobile-search-btn');
        const mobileSearchPanel = document.getElementById('mobile-search-panel');
        const mobileSearchInput = document.querySelector('.mobile-search-input');
        const mobileSearchClose = document.getElementById('mobile-search-close');
        const clearSearchBtn = document.getElementById('clear-search');

        // QRIS Static Data
        const QRIS_STATIC_DATA = "00020101021126610014COM.GO-JEK.WWW01189360091430687178460210G0687178460303UMI51440014ID.CO.QRIS.WWW0215ID10243600706340303UMI5204541153033605802ID5919Warung 68, SAWANGAN6005DEPOK61051651962070703A0163046826";

        // =============================================
        // DATA MANAGEMENT FUNCTIONS
        // =============================================

        // Load data from localStorage
        function loadData() {
            // Load products
            const storedProducts = localStorage.getItem(STORAGE_KEYS.PRODUCTS);
            products = storedProducts ? JSON.parse(storedProducts) : DEFAULT_PRODUCTS;

            // Load carousel items
            const storedCarousel = localStorage.getItem(STORAGE_KEYS.CAROUSEL);
            carouselItems = storedCarousel ? JSON.parse(storedCarousel) : DEFAULT_CAROUSEL_ITEMS;

            // Load admin data
            const storedAdminData = localStorage.getItem(STORAGE_KEYS.ORDERS);
            if (storedAdminData) {
                adminData.orders = JSON.parse(storedAdminData);
                
                // Load other admin data
                adminData.users = JSON.parse(localStorage.getItem(STORAGE_KEYS.USERS) || JSON.stringify(DEFAULT_ADMIN_DATA.users));
                adminData.banners = JSON.parse(localStorage.getItem(STORAGE_KEYS.BANNERS) || '[]');
                adminData.pendingProducts = JSON.parse(localStorage.getItem(STORAGE_KEYS.PENDING_PRODUCTS) || '[]');
            } else {
                adminData = {...DEFAULT_ADMIN_DATA};
            }

            // Load cart
            const storedCart = localStorage.getItem(STORAGE_KEYS.CART);
            cart = storedCart ? JSON.parse(storedCart) : [];

            // Load wishlist
            const storedWishlist = localStorage.getItem(STORAGE_KEYS.WISHLIST);
            wishlist = storedWishlist ? JSON.parse(storedWishlist) : [];
        }

        // Save data to localStorage
        function saveData() {
            localStorage.setItem(STORAGE_KEYS.PRODUCTS, JSON.stringify(products));
            localStorage.setItem(STORAGE_KEYS.CAROUSEL, JSON.stringify(carouselItems));
            localStorage.setItem(STORAGE_KEYS.ORDERS, JSON.stringify(adminData.orders));
            localStorage.setItem(STORAGE_KEYS.USERS, JSON.stringify(adminData.users));
            localStorage.setItem(STORAGE_KEYS.BANNERS, JSON.stringify(adminData.banners));
            localStorage.setItem(STORAGE_KEYS.PENDING_PRODUCTS, JSON.stringify(adminData.pendingProducts));
            localStorage.setItem(STORAGE_KEYS.CART, JSON.stringify(cart));
            localStorage.setItem(STORAGE_KEYS.WISHLIST, JSON.stringify(wishlist));
        }

        // Save products only
        function saveProducts() {
            localStorage.setItem(STORAGE_KEYS.PRODUCTS, JSON.stringify(products));
        }

        // Save carousel only
        function saveCarousel() {
            localStorage.setItem(STORAGE_KEYS.CAROUSEL, JSON.stringify(carouselItems));
        }

        // Save admin data only
        function saveAdminData() {
            localStorage.setItem(STORAGE_KEYS.ORDERS, JSON.stringify(adminData.orders));
            localStorage.setItem(STORAGE_KEYS.USERS, JSON.stringify(adminData.users));
            localStorage.setItem(STORAGE_KEYS.BANNERS, JSON.stringify(adminData.banners));
            localStorage.setItem(STORAGE_KEYS.PENDING_PRODUCTS, JSON.stringify(adminData.pendingProducts));
        }

        // Save cart only
        function saveCart() {
            localStorage.setItem(STORAGE_KEYS.CART, JSON.stringify(cart));
            updateCartCount();
        }

        // Save wishlist only
        function saveWishlist() {
            localStorage.setItem(STORAGE_KEYS.WISHLIST, JSON.stringify(wishlist));
            updateWishlistCount();
        }

        // =============================================
        // INITIALIZATION
        // =============================================

        // Initialize from localStorage
        function initializeApp() {
            loadData();
            
            updateCartCount();
            updateWishlistCount();

            renderProducts();
            renderCarousel();
            setupEventListeners();
            setupScrollBehavior();
            setupAdminEventListeners();
            startCarousel();
            renderReceipts();
        }

        // Update cart count display
        function updateCartCount() {
            const totalItems = cart.reduce((total, item) => total + item.quantity, 0);
            if (cartCountElement) {
                cartCountElement.textContent = totalItems;
            }
        }

        // Update wishlist count display
        function updateWishlistCount() {
            if (wishlistCountElement) {
                wishlistCountElement.textContent = wishlist.length;
            }
        }

        // =============================================
        // RENDER FUNCTIONS
        // =============================================

        // Render carousel
        function renderCarousel() {
            if (!carouselSlides || !carouselDots) return;
            
            carouselSlides.innerHTML = '';
            carouselDots.innerHTML = '';
            
            carouselItems.forEach((item, index) => {
                // Create slide
                const slide = document.createElement('div');
                slide.className = 'carousel-slide';
                slide.innerHTML = `
                    <img src="${item.image}" alt="Promo ${index + 1}">
                    <div class="carousel-content">
                        <h2>${item.title}</h2>
                        <p>${item.description}</p>
                        <a href="#" class="hero-btn">Beli Sekarang</a>
                    </div>
                `;
                carouselSlides.appendChild(slide);
                
                // Create dot
                const dot = document.createElement('div');
                dot.className = 'carousel-dot';
                if (index === 0) dot.classList.add('active');
                dot.addEventListener('click', () => {
                    goToCarouselSlide(index);
                });
                carouselDots.appendChild(dot);
            });
            
            updateCarousel();
        }

        // Update carousel display
        function updateCarousel() {
            if (!carouselSlides) return;
            
            carouselSlides.style.transform = `translateX(-${currentCarouselIndex * 100}%)`;
            
            // Update dots
            const dots = document.querySelectorAll('.carousel-dot');
            dots.forEach((dot, index) => {
                dot.classList.toggle('active', index === currentCarouselIndex);
            });
        }

        // Go to specific carousel slide
        function goToCarouselSlide(index) {
            currentCarouselIndex = index;
            if (currentCarouselIndex >= carouselItems.length) currentCarouselIndex = 0;
            if (currentCarouselIndex < 0) currentCarouselIndex = carouselItems.length - 1;
            updateCarousel();
        }

        // Go to next carousel slide
        function nextCarouselSlide() {
            goToCarouselSlide(currentCarouselIndex + 1);
        }

        // Start carousel autoplay
        function startCarousel() {
            stopCarousel();
            carouselInterval = setInterval(nextCarouselSlide, 5000);
        }

        // Stop carousel autoplay
        function stopCarousel() {
            clearInterval(carouselInterval);
        }

        // Render products
        function renderProducts() {
            // Clear existing products
            if (featuredProductsGrid) featuredProductsGrid.innerHTML = '';
            if (promoProductsGrid) promoProductsGrid.innerHTML = '';
            if (allProductsGrid) allProductsGrid.innerHTML = '';
            if (wishlistGrid) wishlistGrid.innerHTML = '';

            // Render featured products (first 8)
            products.slice(0, 8).forEach(product => {
                if (featuredProductsGrid) {
                    featuredProductsGrid.appendChild(createProductCard(product));
                }
            });

            // Render promo products (products with discount)
            products.filter(p => p.originalPrice).slice(0, 8).forEach(product => {
                if (promoProductsGrid) {
                    promoProductsGrid.appendChild(createProductCard(product));
                }
            });

            // Render all products
            products.forEach(product => {
                if (allProductsGrid) {
                    allProductsGrid.appendChild(createProductCard(product));
                }
            });

            // Render wishlist products
            if (wishlistGrid) {
                if (wishlist.length === 0) {
                    wishlistGrid.innerHTML = `
                        <div class="no-results" style="grid-column: 1 / -1;">
                            <i class="fas fa-heart" style="font-size: 48px; color: #ccc; margin-bottom: 16px;"></i>
                            <h3>Wishlist Kosong</h3>
                            <p>Tambahkan produk ke wishlist untuk melihatnya di sini</p>
                        </div>
                    `;
                } else {
                    products.filter(product => wishlist.includes(product.id)).forEach(product => {
                        wishlistGrid.appendChild(createProductCard(product));
                    });
                }
            }
        }

        // Create product card element
        function createProductCard(product) {
            const card = document.createElement('div');
            card.className = 'product-card';
            card.setAttribute('data-id', product.id);

            // Check if product is in wishlist
            const isLiked = wishlist.includes(product.id);

            let priceHtml = `<div class="current-price">Rp ${product.price.toLocaleString()}</div>`;

            if (product.originalPrice) {
                const discount = Math.round((1 - product.price / product.originalPrice) * 100);
                priceHtml = `
                    <div class="current-price">Rp ${product.price.toLocaleString()}</div>
                    <div class="original-price">Rp ${product.originalPrice.toLocaleString()}</div>
                    <div class="discount">${discount}%</div>
                `;
            }

            card.innerHTML = `
                ${product.badge ? `<div class="product-badge">${product.badge}</div>` : ''}
                <div class="product-image">
                    <img src="${product.image}" alt="${product.name}" onerror="this.src='https://via.placeholder.com/200x200/cccccc/999999?text=Gambar+Tidak+Tersedia'">
                    <button class="like-button ${isLiked ? 'liked' : ''}" data-id="${product.id}">
                        <i class="${isLiked ? 'fas' : 'far'} fa-heart"></i>
                    </button>
                </div>
                <div class="product-info">
                    <h3 class="product-title">${product.name}</h3>
                    <div class="product-price">
                        ${priceHtml}
                    </div>
                    <button class="add-to-cart" data-id="${product.id}">+ Tambah</button>
                </div>
            `;

            // Add event listeners
            const addToCartButton = card.querySelector('.add-to-cart');
            if (addToCartButton) {
                addToCartButton.addEventListener('click', function() {
                    const productId = parseInt(this.getAttribute('data-id'));
                    addToCart(productId);
                });
            }

            const likeButton = card.querySelector('.like-button');
            if (likeButton) {
                likeButton.addEventListener('click', function() {
                    const productId = parseInt(this.getAttribute('data-id'));
                    toggleWishlist(productId);
                    
                    // Update heart icon
                    const isLiked = wishlist.includes(productId);
                    this.innerHTML = `<i class="${isLiked ? 'fas' : 'far'} fa-heart"></i>`;
                    this.classList.toggle('liked', isLiked);

                    // Jika di halaman wishlist, perbarui tampilan
                    if (currentPage === 'wishlist') {
                        renderProducts();
                    }
                });
            }

            return card;
        }

        // Add to cart functionality
        function addToCart(productId) {
            const product = products.find(p => p.id === productId);

            if (product) {
                // Check if product is already in cart
                const existingItem = cart.find(item => item.id === productId);

                if (existingItem) {
                    existingItem.quantity++;
                } else {
                    cart.push({
                        id: productId,
                        name: product.name,
                        price: product.price,
                        quantity: 1,
                        image: product.image
                    });
                }

                saveCart();
                alert('Produk berhasil ditambahkan ke keranjang!');
            }
        }

        // Toggle wishlist functionality
        function toggleWishlist(productId) {
            const product = products.find(p => p.id === productId);

            if (product) {
                const index = wishlist.indexOf(productId);

                if (index > -1) {
                    // Remove from wishlist
                    wishlist.splice(index, 1);
                    alert('Produk dihapus dari wishlist!');
                } else {
                    // Add to wishlist
                    wishlist.push(productId);
                    alert('Produk ditambahkan ke wishlist!');
                }

                saveWishlist();
            }
        }

        // Render cart
        function renderCart() {
            if (!cartBody) return;
            
            if (cart.length === 0) {
                cartBody.innerHTML = `
                    <div class="empty-cart">
                        <i class="fas fa-shopping-cart"></i>
                        <h4>Keranjang Belanja Kosong</h4>
                        <p>Mulai belanja sekarang dan tambahkan produk ke keranjang Anda</p>
                    </div>
                `;
            } else {
                let cartHTML = '';
                
                cart.forEach(item => {
                    cartHTML += `
                        <div class="cart-item">
                            <div class="cart-item-image">
                                <img src="${item.image}" alt="${item.name}" onerror="this.src='https://via.placeholder.com/80x80/cccccc/999999?text=Gambar+Tidak+Tersedia'">
                            </div>
                            <div class="cart-item-details">
                                <h4 class="cart-item-title">${item.name}</h4>
                                <div class="cart-item-price">Rp ${item.price.toLocaleString()} x ${item.quantity}</div>
                                <div class="cart-item-actions">
                                    <div class="quantity-control">
                                        <button class="quantity-btn minus" data-id="${item.id}">-</button>
                                        <input type="text" class="quantity-input" value="${item.quantity}" readonly>
                                        <button class="quantity-btn plus" data-id="${item.id}">+</button>
                                    </div>
                                    <button class="remove-btn" data-id="${item.id}">
                                        <i class="fas fa-trash"></i> Hapus
                                    </button>
                                </div>
                            </div>
                        </div>
                    `;
                });
                
                // Calculate totals
                const subtotal = cart.reduce((total, item) => total + (item.price * item.quantity), 0);
                const shipping = subtotal > 100000 ? 0 : 15000;
                const total = subtotal + shipping;
                
                cartHTML += `
                    <div class="cart-summary">
                        <div class="summary-item">
                            <span>Subtotal</span>
                            <span>Rp ${subtotal.toLocaleString()}</span>
                        </div>
                        <div class="summary-item">
                            <span>Pengiriman</span>
                            <span>${shipping === 0 ? 'Gratis' : 'Rp ' + shipping.toLocaleString()}</span>
                        </div>
                        <div class="summary-total">
                            <span>Total</span>
                            <span>Rp ${total.toLocaleString()}</span>
                        </div>
                        <button class="checkout-btn" id="start-checkout">Lanjut ke Pembayaran</button>
                    </div>
                `;
                
                cartBody.innerHTML = cartHTML;
                
                // Add event listeners to quantity buttons
                document.querySelectorAll('.quantity-btn.minus').forEach(button => {
                    button.addEventListener('click', function() {
                        const itemId = parseInt(this.getAttribute('data-id'));
                        const cartItem = cart.find(item => item.id === itemId);

                        if (cartItem && cartItem.quantity > 1) {
                            cartItem.quantity--;
                            saveCart();
                            renderCart();
                        }
                    });
                });

                document.querySelectorAll('.quantity-btn.plus').forEach(button => {
                    button.addEventListener('click', function() {
                        const itemId = parseInt(this.getAttribute('data-id'));
                        const cartItem = cart.find(item => item.id === itemId);

                        if (cartItem) {
                            cartItem.quantity++;
                            saveCart();
                            renderCart();
                        }
                    });
                });

                document.querySelectorAll('.remove-btn').forEach(button => {
                    button.addEventListener('click', function() {
                        const itemId = parseInt(this.getAttribute('data-id'));
                        const product = products.find(p => p.id === itemId);
                        
                        cart = cart.filter(item => item.id !== itemId);
                        saveCart();
                        renderCart();
                    });
                });

                // Add event listener to checkout button
                const startCheckoutBtn = document.getElementById('start-checkout');
                if (startCheckoutBtn) {
                    startCheckoutBtn.addEventListener('click', function() {
                        if (cartModal) cartModal.classList.remove('active');
                        if (checkoutModal) checkoutModal.classList.add('active');
                    });
                }
            }
        }

        // Generate Dynamic QRIS
        async function generateDynamicQRIS(nominal) {
            try {
                const response = await fetch(`https://cekid-ariepulsa.my.id/api/?qris_data=${encodeURIComponent(QRIS_STATIC_DATA)}&nominal=${nominal}`);
                const data = await response.json();
                
                if (data.status === 'success') {
                    return data.link_qris;
                } else {
                    console.error('API returned non-success status:', data);
                    return null;
                }
            } catch (error) {
                console.error('Error fetching dynamic QRIS:', error);
                return null;
            }
        }

        // Simulate payment verification
        function simulatePaymentVerification() {
            const verificationStatus = document.querySelector('.verification-status');
            
            verificationStatus.className = 'verification-status verifying';
            verificationStatus.innerHTML = '<i class="fas fa-spinner"></i><span>Memverifikasi pembayaran...</span>';
            
            // Simulate API call to verify payment
            return new Promise((resolve) => {
                setTimeout(() => {
                    // 80% chance of success, 20% chance of failure for demo purposes
                    const isSuccess = Math.random() > 0.2;
                    
                    if (isSuccess) {
                        verificationStatus.className = 'verification-status success';
                        verificationStatus.innerHTML = '<i class="fas fa-check-circle"></i><span>Pembayaran berhasil diverifikasi</span>';
                        resolve(true);
                    } else {
                        verificationStatus.className = 'verification-status error';
                        verificationStatus.innerHTML = '<i class="fas fa-times-circle"></i><span>Pembayaran gagal diverifikasi</span>';
                        resolve(false);
                    }
                }, 3000);
            });
        }

        // Search function
        function performSearch(searchTerm) {
            const filteredProducts = products.filter(product => 
                product.name.toLowerCase().includes(searchTerm) || 
                product.category.toLowerCase().includes(searchTerm)
            );
            
            // Hide all product sections
            document.getElementById('featured-section').style.display = 'none';
            document.getElementById('promo-section').style.display = 'none';
            document.getElementById('all-products-section').style.display = 'none';
            
            // Show search results section
            searchResultsSection.style.display = 'block';
            
            // Clear search results
            if (searchResultsGrid) searchResultsGrid.innerHTML = '';
            
            // Show search results
            if (filteredProducts.length === 0) {
                if (searchResultsGrid) {
                    searchResultsGrid.innerHTML = `
                        <div class="no-results">
                            <i class="fas fa-search"></i>
                            <h3>Produk tidak ditemukan</h3>
                            <p>Tidak ada hasil untuk "${searchTerm}". Coba dengan kata kunci lain.</p>
                        </div>
                    `;
                }
            } else {
                filteredProducts.forEach(product => {
                    if (searchResultsGrid) {
                        searchResultsGrid.appendChild(createProductCard(product));
                    }
                });
            }
            
            // Scroll to search results section
            searchResultsSection.scrollIntoView({ behavior: 'smooth' });
        }

        // Clear search and show all products
        function clearSearch() {
            searchInput.value = '';
            mobileSearchInput.value = '';
            searchResultsSection.style.display = 'none';
            document.getElementById('featured-section').style.display = 'block';
            document.getElementById('promo-section').style.display = 'block';
            document.getElementById('all-products-section').style.display = 'block';
        }

        // Navigate to page
        function navigateTo(pageId) {
            // Hide all pages
            pages.forEach(page => {
                page.classList.remove('active');
            });
            
            // Show selected page
            document.getElementById(`${pageId}-page`).classList.add('active');
            
            // Update current page
            currentPage = pageId;
            
            // Close mobile menu
            if (mobileMenu) mobileMenu.classList.remove('active');
            document.body.style.overflow = '';
            
            // Render products if needed
            if (pageId === 'wishlist') {
                renderProducts();
            }
            
            // Render receipts if needed
            if (pageId === 'history') {
                renderReceipts();
            }
            
            // If navigating to admin panel, render admin data
            if (pageId === 'admin' && isAdmin) {
                renderAdminDashboard();
            }
        }

        // Render receipts for history page
        function renderReceipts() {
            if (!historyReceipts) return;
            
            const orders = adminData.orders || [];
            
            if (orders.length === 0) {
                historyReceipts.innerHTML = `
                    <div class="no-results">
                        <i class="fas fa-receipt"></i>
                        <h3>Belum ada riwayat transaksi</h3>
                        <p>Setelah melakukan pembelian, struk akan muncul di sini</p>
                    </div>
                `;
                return;
            }
            
            historyReceipts.innerHTML = '';
            
            orders.forEach(order => {
                const receipt = document.createElement('div');
                receipt.className = 'receipt-card';
                
                receipt.innerHTML = `
                    <button class="print-receipt" data-id="${order.id}">
                        <i class="fas fa-print"></i>
                    </button>
                    <div class="receipt-header">
                        <h3>Fresh.in</h3>
                        <p>Struk Pembelian</p>
                        <small>ID: ${order.id}</small>
                        <small>Tanggal: ${order.date}</small>
                    </div>
                    <div class="receipt-details">
                        <div class="receipt-item">
                            <span>Nama Pelanggan:</span>
                            <span>${order.customer.name}</span>
                        </div>
                        <div class="receipt-item">
                            <span>Telepon:</span>
                            <span>${order.customer.phone}</span>
                        </div>
                        <div class="receipt-item">
                            <span>Alamat:</span>
                            <span>${order.customer.address}</span>
                        </div>
                    </div>
                    <div class="receipt-items">
                        <h4>Item Pembelian:</h4>
                        ${order.items.map(item => `
                            <div class="receipt-item">
                                <span>${item.name} x${item.quantity}</span>
                                <span>Rp ${(item.price * item.quantity).toLocaleString()}</span>
                            </div>
                        `).join('')}
                    </div>
                    <div class="receipt-total">
                        <span>Total:</span>
                        <span>Rp ${order.total.toLocaleString()}</span>
                    </div>
                    <div class="receipt-footer">
                        <p>Terima kasih telah berbelanja di Fresh.in</p>
                        <p>www.fresh.in</p>
                    </div>
                `;
                
                historyReceipts.appendChild(receipt);
            });
            
            // Add event listeners to print buttons
            document.querySelectorAll('.print-receipt').forEach(button => {
                button.addEventListener('click', function() {
                    const orderId = this.getAttribute('data-id');
                    printReceipt(orderId);
                });
            });
        }

        // Print receipt
        function printReceipt(orderId) {
            const order = adminData.orders.find(o => o.id == orderId);
            
            if (!order) return;
            
            const printWindow = window.open('', '_blank');
            printWindow.document.write(`
                <!DOCTYPE html>
                <html>
                <head>
                    <title>Struk Fresh.in - ${order.id}</title>
                    <style>
                        body {
                            font-family: Arial, sans-serif;
                            margin: 0;
                            padding: 20px;
                            font-size: 14px;
                        }
                        .receipt {
                            max-width: 300px;
                            margin: 0 auto;
                        }
                        .header {
                            text-align: center;
                            margin-bottom: 15px;
                            border-bottom: 1px dashed #000;
                            padding-bottom: 10px;
                        }
                        .header h2 {
                            margin: 0;
                            color: #4CAF50;
                        }
                        .item {
                            display: flex;
                            justify-content: space-between;
                            margin-bottom: 5px;
                        }
                        .total {
                            display: flex;
                            justify-content: space-between;
                            font-weight: bold;
                            margin-top: 10px;
                            border-top: 1px dashed #000;
                            padding-top: 10px;
                        }
                        .footer {
                            text-align: center;
                            margin-top: 15px;
                            font-size: 12px;
                        }
                        @media print {
                            body {
                                padding: 0;
                            }
                        }
                    </style>
                </head>
                <body>
                    <div class="receipt">
                        <div class="header">
                            <h2>Fresh.in</h2>
                            <p>Struk Pembelian</p>
                            <p>ID: ${order.id}</p>
                            <p>Tanggal: ${order.date}</p>
                        </div>
                        <div class="details">
                            <p><strong>Pelanggan:</strong> ${order.customer.name}</p>
                            <p><strong>Telepon:</strong> ${order.customer.phone}</p>
                        </div>
                        <div class="items">
                            <h4>Item Pembelian:</h4>
                            ${order.items.map(item => `
                                <div class="item">
                                    <span>${item.name} x${item.quantity}</span>
                                    <span>Rp ${(item.price * item.quantity).toLocaleString()}</span>
                                </div>
                            `).join('')}
                        </div>
                        <div class="total">
                            <span>TOTAL:</span>
                            <span>Rp ${order.total.toLocaleString()}</span>
                        </div>
                    </div>
                    <script>
                        window.onload = function() {
                            window.print();
                            setTimeout(function() {
                                window.close();
                            }, 1000);
                        };
                    <\/script>
                </body>
                </html>
            `);
            printWindow.document.close();
        }

        // Setup scroll behavior for header
        function setupScrollBehavior() {
            window.addEventListener('scroll', function() {
                const st = window.pageYOffset || document.documentElement.scrollTop;
                
                if (st > lastScrollTop && st > 50) {
                    // Scroll down - hide header
                    header.classList.add('scrolled');
                } else {
                    // Scroll up - show header
                    header.classList.remove('scrolled');
                }
                
                lastScrollTop = st <= 0 ? 0 : st;
            }, false);
        }

        // =============================================
        // ADMIN FUNCTIONS
        // =============================================

        // Setup admin event listeners
        function setupAdminEventListeners() {
            // Admin link click
            if (adminLink) {
                adminLink.addEventListener('click', function(e) {
                    e.preventDefault();
                    if (isAdmin) {
                        navigateTo('admin');
                    } else {
                        adminLoginModal.classList.add('active');
                    }
                });
            }

            // Close admin login modal
            if (closeAdminLogin) {
                closeAdminLogin.addEventListener('click', function() {
                    adminLoginModal.classList.remove('active');
                });
            }

            // Admin login
            if (adminLoginBtn) {
                adminLoginBtn.addEventListener('click', function() {
                    const username = adminUsername.value;
                    const password = adminPassword.value;
                    
                    if (username === ADMIN_CREDENTIALS.username && password === ADMIN_CREDENTIALS.password) {
                        isAdmin = true;
                        adminLoginModal.classList.remove('active');
                        alert('Login admin berhasil!');
                        
                        // Clear login form
                        adminUsername.value = '';
                        adminPassword.value = '';
                        
                        // Navigate to admin panel
                        navigateTo('admin');
                    } else {
                        alert('Username atau password salah!');
                    }
                });
            }

            // Admin logout
            if (adminLogoutBtn) {
                adminLogoutBtn.addEventListener('click', function() {
                    isAdmin = false;
                    alert('Anda telah logout dari panel admin.');
                    navigateTo('home');
                });
            }

            // Admin navigation
            adminNavLinks.forEach(link => {
                link.addEventListener('click', function(e) {
                    e.preventDefault();
                    
                    // Update active nav link
                    adminNavLinks.forEach(l => l.classList.remove('active'));
                    this.classList.add('active');
                    
                    // Show corresponding section
                    const sectionId = this.getAttribute('data-admin-section');
                    adminSections.forEach(section => {
                        section.classList.remove('active');
                    });
                    document.getElementById(`admin-${sectionId}`).classList.add('active');
                    
                    // If it's the reports section, render the chart
                    if (sectionId === 'reports') {
                        renderSalesChart();
                    }
                    
                    // If it's the products section, render products table
                    if (sectionId === 'products') {
                        renderProductsTable();
                    }
                    
                    // If it's the orders section, render orders table
                    if (sectionId === 'orders') {
                        renderOrdersTable();
                    }
                    
                    // If it's the users section, render users table
                    if (sectionId === 'users') {
                        renderUsersTable();
                    }
                    
                    // If it's the content section, render banners table
                    if (sectionId === 'content') {
                        renderBannersTable();
                    }
                });
            });

            // Add product button
            if (addProductBtn) {
                addProductBtn.addEventListener('click', function() {
                    currentEditingProductId = null;
                    productFormTitle.textContent = 'Tambah Produk Baru';
                    resetProductForm();
                    productFormContainer.style.display = 'block';
                });
            }

            // Cancel product form
            if (cancelProductForm) {
                cancelProductForm.addEventListener('click', function() {
                    productFormContainer.style.display = 'none';
                });
            }

            // Save product
            if (saveProductBtn) {
                saveProductBtn.addEventListener('click', function() {
                    saveProduct();
                });
            }

            // Add banner button
            if (addBannerBtn) {
                addBannerBtn.addEventListener('click', function() {
                    currentEditingBannerId = null;
                    bannerFormTitle.textContent = 'Tambah Banner Baru';
                    resetBannerForm();
                    bannerFormContainer.style.display = 'block';
                });
            }

            // Cancel banner form
            if (cancelBannerForm) {
                cancelBannerForm.addEventListener('click', function() {
                    bannerFormContainer.style.display = 'none';
                });
            }

            // Save banner
            if (saveBannerBtn) {
                saveBannerBtn.addEventListener('click', function() {
                    saveBanner();
                });
            }

            // Report period change
            if (reportPeriod) {
                reportPeriod.addEventListener('change', function() {
                    renderSalesChart();
                });
            }

            // Close modals when clicking outside
            window.addEventListener('click', function(e) {
                if (e.target === adminLoginModal) {
                    adminLoginModal.classList.remove('active');
                }
            });
        }

        // Render admin dashboard
        function renderAdminDashboard() {
            // Update stats
            document.getElementById('total-orders').textContent = adminData.orders.length;
            document.getElementById('total-products').textContent = products.length;
            document.getElementById('total-users').textContent = adminData.users.length;
            
            // Calculate total revenue
            const totalRevenue = adminData.orders.reduce((total, order) => total + order.total, 0);
            document.getElementById('total-revenue').textContent = `Rp ${totalRevenue.toLocaleString()}`;
            
            // Render recent orders table
            const recentOrdersTable = document.getElementById('recent-orders-table');
            if (recentOrdersTable) {
                recentOrdersTable.innerHTML = '';
                
                // Get last 5 orders
                const recentOrders = adminData.orders.slice(0, 5);
                
                recentOrders.forEach(order => {
                    const row = document.createElement('tr');
                    
                    // Map status to Indonesian
                    let statusText = '';
                    let statusClass = '';
                    switch(order.status) {
                        case 'pending':
                            statusText = 'Menunggu';
                            statusClass = 'warning';
                            break;
                        case 'processing':
                            statusText = 'Diproses';
                            statusClass = 'info';
                            break;
                        case 'shipped':
                            statusText = 'Dikirim';
                            statusClass = 'primary';
                            break;
                        case 'delivered':
                            statusText = 'Selesai';
                            statusClass = 'success';
                            break;
                        case 'cancelled':
                            statusText = 'Dibatalkan';
                            statusClass = 'error';
                            break;
                    }
                    
                    row.innerHTML = `
                        <td>${order.id}</td>
                        <td>${order.customer}</td>
                        <td>${order.date}</td>
                        <td>Rp ${order.total.toLocaleString()}</td>
                        <td><span class="status-badge ${statusClass}">${statusText}</span></td>
                        <td>
                            <button class="admin-action-btn btn-edit" data-id="${order.id}">Detail</button>
                        </td>
                    `;
                    
                    recentOrdersTable.appendChild(row);
                });
            }
            
            // Render pending products table
            const pendingProductsTable = document.getElementById('pending-products-table');
            if (pendingProductsTable) {
                pendingProductsTable.innerHTML = '';
                
                adminData.pendingProducts.forEach(product => {
                    const row = document.createElement('tr');
                    
                    row.innerHTML = `
                        <td>${product.name}</td>
                        <td>${product.seller}</td>
                        <td>Rp ${product.price.toLocaleString()}</td>
                        <td>${product.date}</td>
                        <td>
                            <button class="admin-action-btn btn-approve" data-id="${product.id}">Setujui</button>
                            <button class="admin-action-btn btn-reject" data-id="${product.id}">Tolak</button>
                        </td>
                    `;
                    
                    pendingProductsTable.appendChild(row);
                });
                
                // Add event listeners to approve/reject buttons
                document.querySelectorAll('.btn-approve').forEach(btn => {
                    btn.addEventListener('click', function() {
                        const productId = this.getAttribute('data-id');
                        approveProduct(productId);
                    });
                });
                
                document.querySelectorAll('.btn-reject').forEach(btn => {
                    btn.addEventListener('click', function() {
                        const productId = this.getAttribute('data-id');
                        rejectProduct(productId);
                    });
                });
            }
        }

        // Render products table
        function renderProductsTable() {
            const productsTable = document.getElementById('products-table');
            if (!productsTable) return;
            
            productsTable.innerHTML = '';
            
            products.forEach(product => {
                const row = document.createElement('tr');
                
                row.innerHTML = `
                    <td>${product.name}</td>
                    <td>${product.category}</td>
                    <td>Rp ${product.price.toLocaleString()}</td>
                    <td>${product.stock || 'N/A'}</td>
                    <td><span class="status-badge success">Aktif</span></td>
                    <td>
                        <button class="admin-action-btn btn-edit" data-id="${product.id}">Edit</button>
                        <button class="admin-action-btn btn-delete" data-id="${product.id}">Hapus</button>
                    </td>
                `;
                
                productsTable.appendChild(row);
            });
            
            // Add event listeners to edit and delete buttons
            document.querySelectorAll('.btn-edit').forEach(btn => {
                btn.addEventListener('click', function() {
                    const productId = parseInt(this.getAttribute('data-id'));
                    editProduct(productId);
                });
            });
            
            document.querySelectorAll('.btn-delete').forEach(btn => {
                btn.addEventListener('click', function() {
                    const productId = parseInt(this.getAttribute('data-id'));
                    deleteProduct(productId);
                });
            });
        }

        // Render orders table
        function renderOrdersTable() {
            const ordersTable = document.getElementById('orders-table');
            if (!ordersTable) return;
            
            ordersTable.innerHTML = '';
            
            adminData.orders.forEach(order => {
                const row = document.createElement('tr');
                
                // Map status to Indonesian
                let statusText = '';
                let statusClass = '';
                switch(order.status) {
                    case 'pending':
                        statusText = 'Menunggu';
                        statusClass = 'warning';
                        break;
                    case 'processing':
                        statusText = 'Diproses';
                        statusClass = 'info';
                        break;
                    case 'shipped':
                        statusText = 'Dikirim';
                        statusClass = 'primary';
                        break;
                    case 'delivered':
                        statusText = 'Selesai';
                        statusClass = 'success';
                        break;
                    case 'cancelled':
                        statusText = 'Dibatalkan';
                        statusClass = 'error';
                        break;
                }
                
                row.innerHTML = `
                    <td>${order.id}</td>
                    <td>${order.customer}</td>
                    <td>${order.date}</td>
                    <td>${order.items.length} items</td>
                    <td>Rp ${order.total.toLocaleString()}</td>
                    <td><span class="status-badge ${statusClass}">${statusText}</span></td>
                    <td>
                        <button class="admin-action-btn btn-edit" data-id="${order.id}">Detail</button>
                    </td>
                `;
                
                ordersTable.appendChild(row);
            });
        }

        // Render users table
        function renderUsersTable() {
            const usersTable = document.getElementById('users-table');
            if (!usersTable) return;
            
            usersTable.innerHTML = '';
            
            adminData.users.forEach(user => {
                const row = document.createElement('tr');
                
                row.innerHTML = `
                    <td>${user.name}</td>
                    <td>${user.email}</td>
                    <td>${user.role}</td>
                    <td>${user.joinDate}</td>
                    <td><span class="status-badge ${user.status === 'active' ? 'success' : 'error'}">${user.status === 'active' ? 'Aktif' : 'Nonaktif'}</span></td>
                    <td>
                        <button class="admin-action-btn btn-edit" data-id="${user.id}">Edit</button>
                    </td>
                `;
                
                usersTable.appendChild(row);
            });
        }

        // Render banners table
        function renderBannersTable() {
            const bannersTable = document.getElementById('banners-table');
            if (!bannersTable) return;
            
            bannersTable.innerHTML = '';
            
            adminData.banners.forEach(banner => {
                const row = document.createElement('tr');
                
                row.innerHTML = `
                    <td><img src="${banner.image}" alt="${banner.title}" style="width: 100px; height: auto;"></td>
                    <td>${banner.title}</td>
                    <td>${banner.description}</td>
                    <td><span class="status-badge ${banner.status === 'active' ? 'success' : 'error'}">${banner.status === 'active' ? 'Aktif' : 'Nonaktif'}</span></td>
                    <td>
                        <button class="admin-action-btn btn-edit" data-id="${banner.id}">Edit</button>
                        <button class="admin-action-btn btn-delete" data-id="${banner.id}">Hapus</button>
                    </td>
                `;
                
                bannersTable.appendChild(row);
            });
            
            // Add event listeners to edit and delete buttons
            document.querySelectorAll('.btn-edit').forEach(btn => {
                btn.addEventListener('click', function() {
                    const bannerId = this.getAttribute('data-id');
                    editBanner(bannerId);
                });
            });
            
            document.querySelectorAll('.btn-delete').forEach(btn => {
                btn.addEventListener('click', function() {
                    const bannerId = this.getAttribute('data-id');
                    deleteBanner(bannerId);
                });
            });
        }

        // Render sales chart
        function renderSalesChart() {
            const ctx = document.getElementById('sales-chart');
            if (!ctx) return;
            
            // Destroy existing chart if it exists
            if (salesChart) {
                salesChart.destroy();
            }
            
            // Get selected period
            const period = parseInt(reportPeriod.value);
            
            // Generate sample data based on period
            const labels = [];
            const data = [];
            
            const now = new Date();
            for (let i = period - 1; i >= 0; i--) {
                const date = new Date(now);
                date.setDate(date.getDate() - i);
                
                labels.push(date.toLocaleDateString('id-ID', { day: 'numeric', month: 'short' }));
                
                // Generate random sales data
                const sales = Math.floor(Math.random() * 5000000) + 1000000;
                data.push(sales);
            }
            
            // Create new chart
            salesChart = new Chart(ctx, {
                type: 'line',
                data: {
                    labels: labels,
                    datasets: [{
                        label: 'Pendapatan Harian',
                        data: data,
                        borderColor: '#4CAF50',
                        backgroundColor: 'rgba(76, 175, 80, 0.1)',
                        tension: 0.4,
                        fill: true
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            position: 'top',
                        },
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    return `Rp ${context.raw.toLocaleString()}`;
                                }
                            }
                        }
                    },
                    scales: {
                        y: {
                            beginAtZero: true,
                            ticks: {
                                callback: function(value) {
                                    return 'Rp ' + value.toLocaleString();
                                }
                            }
                        }
                    }
                }
            });
        }

        // Edit product
        function editProduct(productId) {
            const product = products.find(p => p.id === productId);
            
            if (product) {
                currentEditingProductId = productId;
                productFormTitle.textContent = 'Edit Produk';
                
                // Fill form with product data
                document.getElementById('product-name').value = product.name;
                document.getElementById('product-category').value = product.category;
                document.getElementById('product-price').value = product.price;
                document.getElementById('product-original-price').value = product.originalPrice || '';
                document.getElementById('product-stock').value = product.stock || '';
                document.getElementById('product-image').value = product.image || '';
                document.getElementById('product-description').value = product.description || '';
                
                // Show form
                productFormContainer.style.display = 'block';
            }
        }

        // Delete product
        function deleteProduct(productId) {
            if (confirm('Apakah Anda yakin ingin menghapus produk ini?')) {
                products = products.filter(p => p.id !== productId);
                saveProducts();
                renderProductsTable();
                alert('Produk berhasil dihapus!');
            }
        }

        // Save product
        function saveProduct() {
            const name = document.getElementById('product-name').value;
            const category = document.getElementById('product-category').value;
            const price = parseInt(document.getElementById('product-price').value);
            const originalPrice = document.getElementById('product-original-price').value ? parseInt(document.getElementById('product-original-price').value) : undefined;
            const stock = document.getElementById('product-stock').value ? parseInt(document.getElementById('product-stock').value) : 0;
            const image = document.getElementById('product-image').value;
            const description = document.getElementById('product-description').value;
            
            if (!name || !category || !price) {
                alert('Harap isi semua field yang wajib diisi!');
                return;
            }
            
            if (currentEditingProductId) {
                // Update existing product
                const productIndex = products.findIndex(p => p.id === currentEditingProductId);
                
                if (productIndex !== -1) {
                    products[productIndex] = {
                        ...products[productIndex],
                        name,
                        category,
                        price,
                        originalPrice,
                        stock,
                        image: image || products[productIndex].image,
                        description: description || products[productIndex].description
                    };
                    
                    alert('Produk berhasil diperbarui!');
                }
            } else {
                // Add new product
                const newId = Math.max(...products.map(p => p.id), 0) + 1;
                
                products.push({
                    id: newId,
                    name,
                    category,
                    price,
                    originalPrice,
                    stock,
                    image: image || 'https://via.placeholder.com/200x200/cccccc/999999?text=Tidak+Ada+Gambar',
                    description
                });
                
                alert('Produk berhasil ditambahkan!');
            }
            
            // Save and update
            saveProducts();
            renderProductsTable();
            productFormContainer.style.display = 'none';
            
            // If on home page, update products display
            if (currentPage === 'home') {
                renderProducts();
            }
        }

        // Reset product form
        function resetProductForm() {
            document.getElementById('product-name').value = '';
            document.getElementById('product-category').value = '';
            document.getElementById('product-price').value = '';
            document.getElementById('product-original-price').value = '';
            document.getElementById('product-stock').value = '';
            document.getElementById('product-image').value = '';
            document.getElementById('product-description').value = '';
        }

        // Edit banner
        function editBanner(bannerId) {
            const banner = adminData.banners.find(b => b.id == bannerId);
            
            if (banner) {
                currentEditingBannerId = bannerId;
                bannerFormTitle.textContent = 'Edit Banner';
                
                // Fill form with banner data
                document.getElementById('banner-title').value = banner.title;
                document.getElementById('banner-description').value = banner.description;
                document.getElementById('banner-image').value = banner.image;
                document.getElementById('banner-status').value = banner.status;
                
                // Show form
                bannerFormContainer.style.display = 'block';
            }
        }

        // Delete banner
        function deleteBanner(bannerId) {
            if (confirm('Apakah Anda yakin ingin menghapus banner ini?')) {
                adminData.banners = adminData.banners.filter(b => b.id != bannerId);
                saveAdminData();
                renderBannersTable();
                alert('Banner berhasil dihapus!');
            }
        }

        // Save banner
        function saveBanner() {
            const title = document.getElementById('banner-title').value;
            const description = document.getElementById('banner-description').value;
            const image = document.getElementById('banner-image').value;
            const status = document.getElementById('banner-status').value;
            
            if (!title || !description || !image) {
                alert('Harap isi semua field yang wajib diisi!');
                return;
            }
            
            if (currentEditingBannerId) {
                // Update existing banner
                const bannerIndex = adminData.banners.findIndex(b => b.id == currentEditingBannerId);
                
                if (bannerIndex !== -1) {
                    adminData.banners[bannerIndex] = {
                        ...adminData.banners[bannerIndex],
                        title,
                        description,
                        image,
                        status
                    };
                    
                    alert('Banner berhasil diperbarui!');
                }
            } else {
                // Add new banner
                const newId = Math.max(...adminData.banners.map(b => b.id), 0) + 1;
                
                adminData.banners.push({
                    id: newId,
                    title,
                    description,
                    image,
                    status
                });
                
                alert('Banner berhasil ditambahkan!');
            }
            
            // Save and update
            saveAdminData();
            renderBannersTable();
            bannerFormContainer.style.display = 'none';
            
            // If on home page, update carousel
            if (currentPage === 'home') {
                renderCarousel();
            }
        }

        // Reset banner form
        function resetBannerForm() {
            document.getElementById('banner-title').value = '';
            document.getElementById('banner-description').value = '';
            document.getElementById('banner-image').value = '';
            document.getElementById('banner-status').value = 'active';
        }

        // Approve product
        function approveProduct(productId) {
            const productIndex = adminData.pendingProducts.findIndex(p => p.id == productId);
            
            if (productIndex !== -1) {
                const product = adminData.pendingProducts[productIndex];
                
                // Add to products
                const newId = Math.max(...products.map(p => p.id), 0) + 1;
                products.push({
                    id: newId,
                    name: product.name,
                    category: product.category,
                    price: product.price,
                    image: product.image || 'https://via.placeholder.com/200x200/cccccc/999999?text=Tidak+Ada+Gambar',
                    description: product.description || ''
                });
                
                // Remove from pending
                adminData.pendingProducts.splice(productIndex, 1);
                
                // Save and update
                saveProducts();
                saveAdminData();
                renderAdminDashboard();
                alert('Produk berhasil disetujui!');
            }
        }

        // Reject product
        function rejectProduct(productId) {
            if (confirm('Apakah Anda yakin ingin menolak produk ini?')) {
                adminData.pendingProducts = adminData.pendingProducts.filter(p => p.id != productId);
                saveAdminData();
                renderAdminDashboard();
                alert('Produk berhasil ditolak!');
            }
        }

        // =============================================
        // EVENT LISTENERS
        // =============================================

        // Setup event listeners
        function setupEventListeners() {
            // Mobile menu toggle
            if (mobileMenuBtn) {
                mobileMenuBtn.addEventListener('click', function() {
                    mobileMenu.classList.toggle('active');
                    document.body.style.overflow = mobileMenu.classList.contains('active') ? 'hidden' : '';
                });
            }

            if (mobileMenuClose) {
                mobileMenuClose.addEventListener('click', function() {
                    mobileMenu.classList.remove('active');
                    document.body.style.overflow = '';
                });
            }

            // Mobile search toggle
            if (mobileSearchBtn) {
                mobileSearchBtn.addEventListener('click', function() {
                    mobileSearchPanel.classList.add('active');
                });
            }

            if (mobileSearchClose) {
                mobileSearchClose.addEventListener('click', function() {
                    mobileSearchPanel.classList.remove('active');
                });
            }

            // Clear search
            if (clearSearchBtn) {
                clearSearchBtn.addEventListener('click', function(e) {
                    e.preventDefault();
                    clearSearch();
                });
            }

            // Mobile search
            if (mobileSearchInput) {
                mobileSearchInput.addEventListener('keypress', function(e) {
                    if (e.key === 'Enter') {
                        performSearch(this.value.toLowerCase());
                        mobileSearchPanel.classList.remove('active');
                    }
                });
            }

            // Search functionality
            if (searchInput) {
                searchInput.addEventListener('keypress', function(e) {
                    if (e.key === 'Enter') {
                        performSearch(this.value.toLowerCase());
                    }
                });
            }

            if (searchBtn) {
                searchBtn.addEventListener('click', function() {
                    performSearch(searchInput.value.toLowerCase());
                });
            }

            // Cart functionality
            if (cartLink) {
                cartLink.addEventListener('click', function(e) {
                    e.preventDefault();
                    renderCart();
                    cartModal.classList.add('active');
                });
            }

            if (closeCartBtn) {
                closeCartBtn.addEventListener('click', function() {
                    cartModal.classList.remove('active');
                });
            }

            // Wishlist functionality
            if (wishlistLink) {
                wishlistLink.addEventListener('click', function(e) {
                    e.preventDefault();
                    navigateTo('wishlist');
                });
            }

            // Carousel controls
            if (carouselPrev) {
                carouselPrev.addEventListener('click', function() {
                    stopCarousel();
                    goToCarouselSlide(currentCarouselIndex - 1);
                    startCarousel();
                });
            }

            if (carouselNext) {
                carouselNext.addEventListener('click', function() {
                    stopCarousel();
                    goToCarouselSlide(currentCarouselIndex + 1);
                    startCarousel();
                });
            }

            // Pause carousel on hover
            const carouselContainer = document.querySelector('.carousel-container');
            if (carouselContainer) {
                carouselContainer.addEventListener('mouseenter', stopCarousel);
                carouselContainer.addEventListener('mouseleave', startCarousel);
            }

            // Checkout functionality
            if (closeCheckoutBtn) {
                closeCheckoutBtn.addEventListener('click', function() {
                    checkoutModal.classList.remove('active');
                });
            }

            // Checkout steps
            const nextToPaymentBtn = document.getElementById('next-to-payment');
            if (nextToPaymentBtn) {
                nextToPaymentBtn.addEventListener('click', function() {
                    // Validate customer info
                    const customerName = document.getElementById('customer-name').value;
                    const customerEmail = document.getElementById('customer-email').value;
                    const customerPhone = document.getElementById('customer-phone').value;
                    const customerAddress = document.getElementById('customer-address').value;
                    
                    if (!customerName || !customerEmail || !customerPhone || !customerAddress) {
                        alert('Harap isi semua informasi pelanggan!');
                        return;
                    }
                    
                    // Store customer info
                    orderData.customer = {
                        name: customerName,
                        email: customerEmail,
                        phone: customerPhone,
                        address: customerAddress
                    };
                    
                    // Go to payment step
                    document.getElementById('checkout-step-1').style.display = 'none';
                    document.getElementById('checkout-step-2').style.display = 'block';
                    document.getElementById('step-1').classList.remove('active');
                    document.getElementById('step-2').classList.add('active');
                    currentCheckoutStep = 2;
                });
            }

            const backToInfoBtn = document.getElementById('back-to-info');
            if (backToInfoBtn) {
                backToInfoBtn.addEventListener('click', function() {
                    document.getElementById('checkout-step-2').style.display = 'none';
                    document.getElementById('checkout-step-1').style.display = 'block';
                    document.getElementById('step-2').classList.remove('active');
                    document.getElementById('step-1').classList.add('active');
                    currentCheckoutStep = 1;
                });
            }

            const nextToConfirmBtn = document.getElementById('next-to-confirm');
            if (nextToConfirmBtn) {
                nextToConfirmBtn.addEventListener('click', async function() {
                    const paymentMethod = document.querySelector('input[name="payment-method"]:checked').value;
                    
                    // Store payment method
                    orderData.paymentMethod = paymentMethod;
                    
                    // If QRIS, generate QR code
                    if (paymentMethod === 'qris') {
                        const qrisPreview = document.getElementById('qris-preview');
                        const qrisImage = document.getElementById('qris-image');
                        
                        // Calculate total
                        const subtotal = cart.reduce((total, item) => total + (item.price * item.quantity), 0);
                        const shipping = subtotal > 100000 ? 0 : 15000;
                        const total = subtotal + shipping;
                        
                        // Generate QRIS
                        const qrImageUrl = await generateDynamicQRIS(total);
                        
                        if (qrImageUrl) {
                            qrisImage.src = qrImageUrl;
                            qrisPreview.style.display = 'block';
                        } else {
                            alert('Gagal menghasilkan QRIS. Silakan coba metode pembayaran lain.');
                            return;
                        }
                    }
                    
                    // Show verification section
                    document.getElementById('payment-verification').style.display = 'block';
                    
                    // Verify payment (simulated)
                    const isPaymentVerified = await simulatePaymentVerification();
                    
                    if (isPaymentVerified) {
                        // Go to confirmation step
                        document.getElementById('checkout-step-2').style.display = 'none';
                        document.getElementById('checkout-step-3').style.display = 'block';
                        document.getElementById('step-2').classList.remove('active');
                        document.getElementById('step-3').classList.add('active');
                        currentCheckoutStep = 3;
                        
                        // Render order summary
                        renderOrderSummary();
                    } else {
                        alert('Pembayaran gagal. Silakan coba lagi.');
                    }
                });
            }

            const backToPaymentBtn = document.getElementById('back-to-payment');
            if (backToPaymentBtn) {
                backToPaymentBtn.addEventListener('click', function() {
                    document.getElementById('checkout-step-3').style.display = 'none';
                    document.getElementById('checkout-step-2').style.display = 'block';
                    document.getElementById('step-3').classList.remove('active');
                    document.getElementById('step-2').classList.add('active');
                    currentCheckoutStep = 2;
                });
            }

            const confirmOrderBtn = document.getElementById('confirm-order');
            if (confirmOrderBtn) {
                confirmOrderBtn.addEventListener('click', function() {
                    // Create order
                    const subtotal = cart.reduce((total, item) => total + (item.price * item.quantity), 0);
                    const shipping = subtotal > 100000 ? 0 : 15000;
                    const total = subtotal + shipping;
                    
                    const newOrder = {
                        id: 'ORD' + Date.now(),
                        date: new Date().toLocaleDateString('id-ID'),
                        customer: orderData.customer.name,
                        items: [...cart],
                        subtotal: subtotal,
                        shipping: shipping,
                        total: total,
                        paymentMethod: orderData.paymentMethod,
                        status: orderData.paymentMethod === 'cod' ? 'pending' : 'processing'
                    };
                    
                    // Add to admin data
                    adminData.orders.unshift(newOrder);
                    saveAdminData();
                    
                    // Clear cart
                    cart = [];
                    saveCart();
                    
                    // Close checkout modal
                    checkoutModal.classList.remove('active');
                    
                    // Show success message
                    alert('Pesanan berhasil dibuat! Terima kasih telah berbelanja di Fresh.in.');
                    
                    // Reset checkout
                    resetCheckout();
                });
            }

            const cancelCheckoutBtn = document.getElementById('cancel-checkout');
            if (cancelCheckoutBtn) {
                cancelCheckoutBtn.addEventListener('click', function() {
                    checkoutModal.classList.remove('active');
                    resetCheckout();
                });
            }

            // Payment method selection
            document.querySelectorAll('.payment-option').forEach(option => {
                option.addEventListener('click', function() {
                    document.querySelectorAll('.payment-option').forEach(opt => {
                        opt.classList.remove('selected');
                    });
                    this.classList.add('selected');
                    
                    const radio = this.querySelector('input[type="radio"]');
                    radio.checked = true;
                    
                    // Show QRIS preview if selected
                    if (this.getAttribute('data-method') === 'qris') {
                        document.getElementById('qris-preview').style.display = 'block';
                    } else {
                        document.getElementById('qris-preview').style.display = 'none';
                    }
                });
            });

            // Navigation links
            document.querySelectorAll('a[data-page]').forEach(link => {
                link.addEventListener('click', function(e) {
                    e.preventDefault();
                    const pageId = this.getAttribute('data-page');
                    navigateTo(pageId);
                });
            });

            // Category links
            document.querySelectorAll('a[data-category]').forEach(link => {
                link.addEventListener('click', function(e) {
                    e.preventDefault();
                    const category = this.getAttribute('data-category');
                    performSearch(category);
                });
            });

            // Close modals when clicking outside
            window.addEventListener('click', function(e) {
                if (e.target === cartModal) {
                    cartModal.classList.remove('active');
                }
                if (e.target === checkoutModal) {
                    checkoutModal.classList.remove('active');
                    resetCheckout();
                }
            });
        }

        // Render order summary
        function renderOrderSummary() {
            const orderSummary = document.getElementById('order-summary');
            
            if (!orderSummary) return;
            
            const subtotal = cart.reduce((total, item) => total + (item.price * item.quantity), 0);
            const shipping = subtotal > 100000 ? 0 : 15000;
            const total = subtotal + shipping;
            
            let summaryHTML = `
                <h4>Ringkasan Pesanan</h4>
                <div class="summary-item">
                    <span>Nama:</span>
                    <span>${orderData.customer.name}</span>
                </div>
                <div class="summary-item">
                    <span>Telepon:</span>
                    <span>${orderData.customer.phone}</span>
                </div>
                <div class="summary-item">
                    <span>Alamat:</span>
                    <span>${orderData.customer.address}</span>
                </div>
                <div class="summary-item">
                    <span>Metode Pembayaran:</span>
                    <span>${orderData.paymentMethod === 'qris' ? 'QRIS' : 'Cash on Delivery'}</span>
                </div>
                <h4 style="margin-top: 15px;">Detail Pembelian</h4>
            `;
            
            cart.forEach(item => {
                summaryHTML += `
                    <div class="summary-item">
                        <span>${item.name} x${item.quantity}</span>
                        <span>Rp ${(item.price * item.quantity).toLocaleString()}</span>
                    </div>
                `;
            });
            
            summaryHTML += `
                <div class="summary-item">
                    <span>Subtotal:</span>
                    <span>Rp ${subtotal.toLocaleString()}</span>
                </div>
                <div class="summary-item">
                    <span>Pengiriman:</span>
                    <span>${shipping === 0 ? 'Gratis' : 'Rp ' + shipping.toLocaleString()}</span>
                </div>
                <div class="summary-total">
                    <span>Total:</span>
                    <span>Rp ${total.toLocaleString()}</span>
                </div>
            `;
            
            orderSummary.innerHTML = summaryHTML;
        }

        // Reset checkout process
        function resetCheckout() {
            // Reset form
            document.getElementById('customer-name').value = '';
            document.getElementById('customer-email').value = '';
            document.getElementById('customer-phone').value = '';
            document.getElementById('customer-address').value = '';
            
            // Reset payment method
            document.querySelectorAll('.payment-option').forEach(opt => {
                opt.classList.remove('selected');
            });
            document.querySelector('.payment-option[data-method="qris"]').classList.add('selected');
            document.getElementById('payment-qris').checked = true;
            
            // Hide QRIS preview and verification
            document.getElementById('qris-preview').style.display = 'none';
            document.getElementById('payment-verification').style.display = 'none';
            
            // Reset to first step
            document.getElementById('checkout-step-1').style.display = 'block';
            document.getElementById('checkout-step-2').style.display = 'none';
            document.getElementById('checkout-step-3').style.display = 'none';
            document.getElementById('step-1').classList.add('active');
            document.getElementById('step-2').classList.remove('active');
            document.getElementById('step-3').classList.remove('active');
            currentCheckoutStep = 1;
            
            // Clear order data
            orderData = {};
        }

        // =============================================
        // INITIALIZE APP
        // =============================================

        // Initialize the app when DOM is loaded
        document.addEventListener('DOMContentLoaded', initializeApp);
    </script>
</body>
</html>
