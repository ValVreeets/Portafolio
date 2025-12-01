/**
 * Portfolio Main JavaScript
 * Este archivo maneja la interactividad del portafolio
 */

// ============================================
// MENÚ DE NAVEGACIÓN MÓVIL
// ============================================

/**
 * Inicializa el menú hamburguesa para dispositivos móviles
 */
function initMobileMenu() {
    const menuToggle = document.getElementById('menuToggle');
    const navLinks = document.getElementById('navLinks');
    
    console.log('MenuToggle encontrado:', menuToggle);
    console.log('NavLinks encontrado:', navLinks);
    
    if (menuToggle && navLinks) {
        // Toggle del menú al hacer clic en el botón hamburguesa
        menuToggle.addEventListener('click', (e) => {
            e.preventDefault();
            e.stopPropagation();
            
            navLinks.classList.toggle('active');
            menuToggle.classList.toggle('active');
            
            console.log('Menú activado:', navLinks.classList.contains('active'));
        });
        // Cerrar menú al hacer clic fuera de él
        document.addEventListener('click', (e) => {
            if (!menuToggle.contains(e.target) && !navLinks.contains(e.target)) {
                navLinks.classList.remove('active');
                menuToggle.classList.remove('active');
            }
        });
    }
}

// ============================================
// NAVEGACIÓN CON SCROLL SUAVE
// ============================================

/**
 * Añade efecto de scroll suave a los enlaces de navegación
 */
function initSmoothScroll() {
    const navLinks = document.querySelectorAll('a[href^="#"]');
    
    navLinks.forEach(link => {
        link.addEventListener('click', (e) => {
            e.preventDefault();
            
            const targetId = link.getAttribute('href');
            const targetSection = document.querySelector(targetId);
            
            if (targetSection) {
                const navbarHeight = document.querySelector('.navbar').offsetHeight;
                const targetPosition = targetSection.offsetTop - navbarHeight;
                
                window.scrollTo({
                    top: targetPosition,
                    behavior: 'smooth'
                });
            }
        });
    });
}

// ============================================
// NAVBAR CON EFECTO AL HACER SCROLL
// ============================================

/**
 * Añade efecto de transparencia/sombra a la navbar al hacer scroll
 */
function initNavbarScroll() {
    const navbar = document.getElementById('navbar');
    let lastScroll = 0;
    
    window.addEventListener('scroll', () => {
        const currentScroll = window.pageYOffset;
        
        // Añadir clase cuando se hace scroll hacia abajo
        if (currentScroll > 50) {
            navbar.style.boxShadow = '0 4px 20px rgba(0, 0, 0, 0.5)';
        } else {
            navbar.style.boxShadow = 'none';
        }
        
        lastScroll = currentScroll;
    });
}

// ============================================
// ANIMACIÓN DE APARICIÓN AL HACER SCROLL
// ============================================

/**
 * Añade animaciones a los elementos cuando aparecen en el viewport
 */
function initScrollAnimations() {
    const observerOptions = {
        threshold: 0.1,
        rootMargin: '0px 0px -50px 0px'
    };

    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                entry.target.style.opacity = '1';
                entry.target.style.transform = 'translateY(0)';
            }
        });
    }, observerOptions);

    // Observar cards de proyectos
    const projectCards = document.querySelectorAll('.project-card');
    projectCards.forEach(card => {
        card.style.opacity = '0';
        card.style.transform = 'translateY(30px)';
        card.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
        observer.observe(card);
    });

    // Observar cards de "Sobre Mí"
    const aboutCards = document.querySelectorAll('.about-card');
    aboutCards.forEach(card => {
        card.style.opacity = '0';
        card.style.transform = 'translateY(30px)';
        card.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
        observer.observe(card);
    });
}

// ============================================
// INICIALIZACIÓN AL CARGAR LA PÁGINA
// ============================================

/**
 * Función principal que se ejecuta cuando el DOM está listo
 */
document.addEventListener('DOMContentLoaded', () => {
    console.log('Portfolio cargado correctamente');
    
    // Inicializar todas las funcionalidades
    initMobileMenu();
    initSmoothScroll();
    initNavbarScroll();
    initScrollAnimations();
    
    // Log para verificar que el JavaScript está funcionando
    console.log('Todas las funcionalidades inicializadas');
});

// ============================================
// UTILIDADES ADICIONALES
// ============================================

/**
 * Función para validar email (útil si agregas un formulario)
 */
function validateEmail(email) {
    const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return re.test(email);
}

/**
 * Función para copiar texto al clipboard
 */
function copyToClipboard(text) {
    navigator.clipboard.writeText(text).then(() => {
        console.log('Texto copiado al portapapeles');
    }).catch(err => {
        console.error('Error al copiar:', err);
    });
}