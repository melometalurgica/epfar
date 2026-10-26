/* =====================================================================
   ESTADÍSTICAS DE EPFAR (Google Analytics 4)
   1) Creá la propiedad en https://analytics.google.com
   2) Copiá el "ID de medición" (empieza con G-) y pegalo abajo.
   Mientras quede vacío, no se carga nada y la web anda igual.
   Todas las páginas usan este archivo: se completa una sola vez.
   ===================================================================== */
(function () {
  var GA_ID = ''; // ← ej.: 'G-AB12CD34EF'
  if (!GA_ID) return;

  var tag = document.createElement('script');
  tag.async = true;
  tag.src = 'https://www.googletagmanager.com/gtag/js?id=' + GA_ID;
  document.head.appendChild(tag);

  window.dataLayer = window.dataLayer || [];
  function gtag() { window.dataLayer.push(arguments); }
  window.gtag = gtag;
  gtag('js', new Date());
  gtag('config', GA_ID);

  /* Eventos para medir lo importante: clics a WhatsApp, Instagram, YouTube y otros sitios */
  document.addEventListener('click', function (event) {
    var link = event.target.closest ? event.target.closest('a[href]') : null;
    if (!link) return;
    var href = link.href || '';
    var name = null;
    if (/wa\.me|api\.whatsapp\.com/.test(href)) name = 'click_whatsapp';
    else if (/instagram\.com/.test(href)) name = 'click_instagram';
    else if (/youtube\.com|youtu\.be/.test(href)) name = 'click_youtube';
    else if (link.hostname && link.hostname !== location.hostname) name = 'click_enlace_externo';
    if (name) {
      gtag('event', name, {
        link_url: href,
        link_text: (link.textContent || '').trim().slice(0, 80)
      });
    }
  }, true);
})();
