# Front-End Checklist
[![Contributors](https://img.shields.io/github/contributors/thedaviddias/Front-End-Checklist.svg)](https://github.com/thedaviddias/Front-End-Checklist/graphs/contributors)
[![CC0](https://img.shields.io/badge/license-CC0-green.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

The **Front-End Checklist** is an exhaustive list of all elements you need to have / to test before launching your site / page HTML to production.

Он основан на многолетнем опыте разработчиков Front-End, с дополнениями, полученными из некоторых других контрольных списков с открытым исходным кодом.

## Table of Contents

1. **[Как пользоваться](#how-to-use)**
2. **[Head](#head)**
3. **[HTML](#html)**
4. **[Webfonts](#webfonts)**
5. **[CSS](#css)**
6. **[Images](#images)**
7. **[JavaScript](#javascript)**
8. **[Security](#security)**
9. **[Performance](#performance-1)**
10. **[Accessibility](#accessibility)**
11. **[SEO](#seo)**

## How to use?

Все элементы в контрольном списке Front-End необходимы для большинства проектов, но некоторые элементы могут быть опущены или не являются существенными (в случае веб-приложения администрирования вам может не понадобиться RSS-канал, например). Мы решили использовать 3 уровня гибкости:

* ![Low][low_img] означает, что элемент **рекомендуется** , но может быть опущен в некоторых конкретных ситуациях.
* ![Medium][medium_img] означает, что этот пункт **настоятельно рекомендуется** и в конечном итоге может быть опущен в некоторых действительно конкретных случаях. Некоторые элементы, если их пропустить, могут иметь плохие последствия с точки зрения производительности или SEO.
* ![High][high_img] означает, что элемент **не может быть опущен** по любой причине. Вы можете вызвать дисфункцию на своей странице или получить доступность или проблемы с SEO. В первую очередь приоритет тестирования должен быть в этих элементах.

У некоторых ресурсов есть смайлик, который поможет вам понять, какой тип содержимого / помощи вы можете найти в контрольном списке:

* 📖: документация или статья
* 🛠: онлайн-инструмент / тестирования
* 📹: медиа или видеоконтент

---

## Head

> **Notes:** You can find [a list of everything](https://github.com/joshbuchea/HEAD) that could be found in the `<head>` of an HTML document.

### Meta tag

* [ ] **Doctype:** ![High][high_img] Doctype - это HTML5 и находится на вершине всех ваших HTML-страниц..

```html
<!-- Doctype HTML5 -->
<!doctype html>
```

> 📖 [Determining the character encoding - HTML5 W3C](https://www.w3.org/TR/html5/syntax.html#determining-the-character-encoding)

*The next 3 meta tags (Charset, X-UA Compatible and Viewport) need to come first in the head.*

* [ ] **Charset:** ![High][high_img] Объявленная кодировка (UTF-8) объявлена правильно.

```html
<!-- Установить кодировку для документа -->
<meta charset="utf-8">
```

* [ ] **X-UA-Compatible:** ![Medium][medium_img] Представлен метатег X-UA-совместимый.

```html
<!-- Попросите Internet Explorer использовать последний механизм рендеринга -->
<meta http-equiv="x-ua-compatible" content="ie=edge">
```

> 📖 [Specifying legacy document modes (Internet Explorer)](https://msdn.microsoft.com/en-us/library/jj676915(v=vs.85).aspx)

* [ ] **Viewport:** ![High][high_img] Видовое окно объявлено правильно.

```html
<!-- Видовой экран для гибкого веб-дизайна -->
<meta name="viewport" content="width=device-width, initial-scale=1">
```

* [ ] **Title:** ![High][high_img] Заголовок используется на всех страницах (SEO: не более 65 символов, включая название сайта).

```html
<!-- Заголовок документа -->
<title>Заголовок страницы менее 65 символов</title>
```

> 📖 [Title - HTML | MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/title)

* [ ] **Description:** ![High][high_img] Предоставлено метаописание, оно уникально и не имеет более 150 символов.

```html
<!-- Описание Meta -->
<meta name="description" content="Описание страницы менее 150 символов">
```

* [ ] **Favicons:** ![Medium][medium_img]Каждый значок был создан и отображен правильно. Если у вас есть только «favicon.ico», поместите его в корень вашего сайта. Обычно вам не нужно использовать разметку. Тем не менее, по-прежнему хорошей практикой является ссылка на него, используя приведенный ниже пример.Сегодня **формат PNG рекомендуется** в формате `.ico` (размеры: 32x32px).

```html
<!-- Стандартный значок -->
<link rel="icon" type="image/x-icon" href="https://example.com/favicon.ico">
<!-- Рекомендуемый формат значка -->
<link rel="icon" type="image/png" href="https://example.com/favicon.png">
```

> * 🛠 [Favicon Generator](https://www.favicon-generator.org/)
> * 🛠 [RealFaviconGenerator](https://realfavicongenerator.net/)
> * 📖 [Favicon Cheat Sheet](https://github.com/audreyr/favicon-cheat-sheet)
> * 📖 [Favicons, Touch Icons, Tile Icons, etc. Which Do You Need? - CSS Tricks](https://css-tricks.com/favicon-quiz/)
> * 📖 [PNG favicons - caniuse](https://caniuse.com/#feat=link-icon-png)

* [ ] **Apple Touch Icon:** ![Low][low_img] Apple touch значок apple-mobile-web-app-capable представлен. *(Создайте файл Apple Icon с размером не менее 200x200 пикселей, чтобы поддерживать все измерения, которые могут вам понадобиться.)*

```html
<!-- Apple Touch Icon -->
<link rel="apple-touch-icon" href="/custom-icon.png">
```

> 📖 [Configuring Web Applications](https://developer.apple.com/library/content/documentation/AppleApplications/Reference/SafariWebContent/ConfiguringWebApplications/ConfiguringWebApplications.html)

* [ ] **Canonical:** ![Medium][medium_img] Используйте `rel="canonical"`, чтобы избежать дублирования содержимого

```html
<!-- Помогает предотвратить дублирование контента -->
<link rel="canonical" href="http://example.com/2017/09/a-new-article-to-red.html">
```

### HTML tags

* [ ] **Language tag:** ![High][high_img] Языковой тег вашего сайта указан и относится к языку текущей страницы.

```html
<html lang="en">
```

* [ ] **Direction tag:** ![Medium][medium_img] Направление течения указано в теге body (его можно использовать в другом теге HTML).

```html
<html dir="rtl">
```

> 📖 [dir - HTML | MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/dir)

* [ ] **Alternate language:** ![Low][low_img] Языковой тег вашего сайта указан и относится к языку текущей страницы.

```html
<link rel="alternate" href="https://es.example.com/" hreflang="es">
```

* [ ] **Conditional comments:** ![Low][low_img] Условные комментарии присутствуют в IE, если это необходимо.

> 📖 [About conditional comments (Internet Explorer) - MSDN - Microsoft](https://msdn.microsoft.com/en-us/library/ms537512(v=vs.85).aspx)

* [ ] **RSS feed:** ![Low][low_img] Если ваш проект является блогом или имеет статьи, ссылка RSS была предоставлена.


* [ ] **CSS Critical:** ![Medium][medium_img] Критический CSS (или «выше складки») собирает все CSS, используемые для визуализации видимой части страницы. Он встроен перед вашим основным вызовом CSS и между `<style> </ style>` в одной строке (уменьшен).

> 🛠 [Critical by Addy Osmani on Github](https://github.com/addyosmani/critical)

* [ ] **CSS order:** ![High][high_img]Все файлы CSS загружаются перед любыми файлами JavaScript в `<head>`.(За исключением случая, когда иногда файлы JS загружаются асинхронно поверх вашей страницы).

### Social meta

***Facebook OG*** и ***Twitter Cards*** для любого веб-сайта настоятельно рекомендуется. Другие теги социальных медиа можно рассмотреть, если вы нацеливаете определенное присутствие на них и хотите обеспечить отображение.

* [ ] **Facebook Open Graph:** ![Low][low_img] Все Facebook Open Graph (OG) протестированы и никого не хватает или с ложной информацией. Изображения должны быть не менее 600 x 315 пикселей, рекомендуется 1200 x 630 пикселей.

```html
<meta property="og:type" content="website">
<meta property="og:url" content="https://example.com/page.html">
<meta property="og:title" content="Content Title">
<meta property="og:image" content="https://example.com/image.jpg">
<meta property="og:description" content="Description Here">
<meta property="og:site_name" content="Site Name">
<meta property="og:locale" content="en_US">
```

> * 📖 [A Guide to Sharing for Webmasters](https://developers.facebook.com/docs/sharing/webmasters/)
> * 🛠 Проверьте свою страницу с помощью [Facebook OG testing](https://developers.facebook.com/tools/debug/)

* [ ] **Twitter Card:** ![Low][low_img]

```html
<meta name="twitter:card" content="summary">
<meta name="twitter:site" content="@site_account">
<meta name="twitter:creator" content="@individual_account">
<meta name="twitter:url" content="https://example.com/page.html">
<meta name="twitter:title" content="Content Title">
<meta name="twitter:description" content="Content description less than 200 characters">
<meta name="twitter:image" content="https://example.com/image.jpg">
```

> * 📖 [Getting started with cards — Twitter Developers](https://developer.twitter.com/en/docs/tweets/optimize-with-cards/guides/getting-started)
> * 🛠 Test your page with the [Twitter card validator](https://cards-dev.twitter.com/validator)

**[⬆ back to top](#table-of-contents)**

---

## HTML

### Лучшие практики


* [ ] **HTML5 Семантические элементы:** ![High][high_img] Семантические элементы HTML5 используются соответствующим образом (заголовок, раздел, нижний колонтитул, основной ...).

> 📖 [HTML Reference](http://htmlreference.io/)

* [ ] **Страницы ошибок:** ![High][high_img] Ошибка 404 и 5xx. Помните, что страница ошибок 5xx должна иметь встроенный CSS (без внешнего вызова на текущем сервере).

* [ ] **Noopener:** ![Medium][medium_img] Если вы используете внешние ссылки с `target =" _ blank "`, ваша ссылка должна иметь атрибут `rel =" noopener "`, чтобы предотвратить табуляцию вкладок. Если вам нужно поддерживать более старые версии Firefox, используйте `rel =" noopener noreferrer "`.

> 📖 [Подробнее о rel=noopener](https://mathiasbynens.github.io/rel-noopener/)

* [ ] **Очистить комментарии:** ![Low][low_img] Необязательный код необходимо удалить перед отправкой страницы в производство.


### Тестирование HTML

* [ ] **W3C совместимый:** ![High][high_img] Все страницы должны быть протестированы с помощью валидатора W3C для определения возможных проблем в HTML-коде.
> 🛠 [Валидатор W3C](https://validator.w3.org/)

* [ ] **HTML Lint:** ![High][high_img] Я использую инструменты, которые помогут мне проанализировать любые проблемы, которые могут возникнуть в моем HTML-коде.

> 🛠 [Грязная разметка](https://dirtymarkup.com/)

* [ ] **Настольные браузеры:** ![High][high_img] Все страницы были протестированы на всех современных настольных браузерах (Safari, Firefox, Chrome, Internet Explorer, EDGE ...).

* [ ] **Мобильные браузеры:**  ![High][high_img] Все страницы были протестированы во всех мобильных браузерах (собственный браузер, Chrome, Safari ...).

* [ ] **Проверка ссылок:** ![High][high_img] На моей странице нет сломанных ссылок, убедитесь, что у вас нет ошибки 404.

> 🛠 [W3C Link Checker](https://validator.w3.org/checklink)

* [ ] **Тест Adblockers:** ![Medium][medium_img] Ваш веб-сайт правильно показывает ваш контент с включенными рекламными блоками (вы можете предоставить сообщение, призывающее людей отключить их рекламный блок).


- [ ] **Pixel perfect:** ![High][high_img] Страницы близки к пикселю. В зависимости от качества объявлений, вы не можете быть на 100% точным, но ваша страница должна быть близка к вашему шаблону.

> [Pixel Perfect - Расширение Chrome](https://chrome.google.com/webstore/detail/perfectpixel-by-welldonec/dkaagdgjmgdmbnecmcefdhjekcoceebi?hl=en)

**[⬆ вернуться к началу](#table-of-contents)**

---

## Веб-шрифты

* [ ] **Формат Webfont:** ![High][high_img] WOFF, WOFF2 and TTF are supported by all modern browsers.

> * 📖 [WOFF - Формат Web Open Font - Caniuse](https://caniuse.com/#feat=woff).
> * 📖 [WOFF 2.0 - Формат Web Open Font - Caniuse](https://caniuse.com/#feat=woff2).
> * 📖 [TTF/OTF - TrueType и OpenType font support](https://caniuse.com/#feat=ttf)
> * 📖 [Использование @font-face - CSS-Tricks](https://css-tricks.com/snippets/css/using-font-face/)

* [ ] **Размер Webfont:** ![High][high_img] Размеры Webfont не превышают 2 МБ (все варианты включены).

**[⬆ вернуться к началу](#table-of-contents)**

---

## CSS

> **Заметки:** Взгляни на [Рекомендации CSS](https://cssguidelin.es/) и [Советы по Sass](https://sass-guidelin.es/) за которыми следуют большинство разработчиков Front-End. Если у вас есть сомнения в свойствах CSS, вы можете посетить [Справочник CSS](http://cssreference.io/).

* [ ] **Отзывчивый веб-дизайн:** ![High][high_img] Веб-сайт использует отзывчивый веб-дизайн.
* [ ] **Печать CSS:** ![Medium][medium_img] На каждой странице предоставляется таблица стилей печати.
* [ ] **Препроцессоры:** ![Medium][medium_img] На вашей странице используется препроцессор CSS ([Sass](http://sass-lang.com/) является предпочтительным).
* [ ] **Уникальный идентификатор:** ![High][high_img] Если используются идентификаторы, они уникальны для страницы.
* [ ] **Сбросить CSS:** ![High][high_img] Сброс CSS (сброс, нормализация или перезагрузка) используется и обновляется. *(Если вы используете CSS-структуру, такую как Bootstrap или Foundation, в нее уже включен Normalize.)*

> * 📖 [Reset.css](https://meyerweb.com/eric/tools/css/reset/)
> * 📖 [Normalize.css](https://necolas.github.io/normalize.css/)
> * 📖 [Reboot](https://getbootstrap.com/docs/4.0/content/reboot/)

* [ ] **Префикс JS:** ![Low][low_img] Все классы (или id-используемые в файлах JavaScript) начинаются с **js -** и не используются в CSS-файлах.

```html
<div id="js-slider" class="my-slider">
<!-- Or -->
<div id="id-used-by-cms" class="js-slider my-slider">
```

* [ ] **Вставка CSS или строка:** ![High][high_img] Избегайте любой ценой использования встроенного или встроенного CSS: используется только по уважительным причинам (например: background-image для слайдера, критический CSS).

* [ ] **Префиксы поставщиков:** ![High][high_img] Префиксы поставщика CSS используются и генерируются соответственно совместимости с поддержкой браузера.
> 🛠 [Autoprefixer CSS онлайн](https://autoprefixer.github.io/)

### Представление

- [ ] **Concatenation:** ![High][high_img] Файлы CSS объединяются в один файл. *(Not for HTTP/2)*
- [ ] **Минификация:** ![High][high_img] Все файлы CSS уменьшены.
- [ ] **Неблокируемая:** ![Medium][medium_img] Файлы CSS должны быть неблокируемыми, чтобы помешать DOM отнимать время для загрузки.

> * 📖 [loadCSS группой нитей](https://github.com/filamentgroup/loadCSS)
> * 📖 [Пример предварительного загрузки CSS с использованием loadCSS](https://gist.github.com/thedaviddias/c24763b82b9991e53928e66a0bafc9bf)

- [ ] **Неиспользуемый CSS:** ![Low][low_img] Удалить неиспользуемый CSS.

> * 🛠 [UnCSS Online](https://uncss-online.com/) 🛠
> * 🛠 [PurifyCSS](https://github.com/purifycss/purifycss)
> * 🛠 [Chrome DevTools Coverage](https://developers.google.com/web/updates/2017/04/devtools-release-notes#coverage)


### Проверка CSS

* [ ] **Stylelint:** ![High][high_img] Все файлы CSS или SCSS без ошибок.


> * 🛠 [stylelint, a CSS linter](https://stylelint.io/)
> * 📖 [Sass guidelines](https://sass-guidelin.es/)

* [ ] **Отзывчивый веб-дизайн:** ![High][high_img] Все страницы были протестированы на следующих контрольных точках: 320 пикселей, 768 пикселей, 1024 пикселей (может быть больше / отличается в зависимости от вашей аналитики).


* [ ] **CSS Validator:** ![Medium][medium_img] CSS был протестирован и исправлены соответствующие ошибки.


> 🛠 [CSS Validator](https://jigsaw.w3.org/css-validator/)

* [ ] **Направление считывания:** ![High][high_img] Все страницы должны быть протестированы для языков LTR и RTL, если они нуждаются в поддержке.

> * 📖 [Building RTL-Aware Web Apps & Websites: Part 1 | Mozilla Hacks](https://hacks.mozilla.org/2015/09/building-rtl-aware-web-apps-and-websites-part-1/)
> * 📖 [Building RTL-Aware Web Apps & Websites: Part 2 | Mozilla Hacks](https://hacks.mozilla.org/2015/10/building-rtl-aware-web-apps-websites-part-2/)

**[⬆ back to top](#table-of-contents)**

---

## Images

> **Notes:** For a complete understanding of image optimization, check the free ebook **[Essential Image Optimization](https://images.guide/)** from Addy Osmani.

### Best practices

* [ ] **Optimization:** ![High][high_img] All images are optimized to be rendered in the browser. WebP format could be used for critical pages (like Homepage).

> * 🛠 [Imagemin](https://github.com/imagemin/imagemin)
> * 🛠 Use [ImageOptim](https://imageoptim.com/) to optimise your images for free.

* [ ] **Retina:** ![Low][low_img] You provide layout images x2 or 3x, support retina display.
* [ ] **Sprite:** ![Medium][medium_img] Small images are in a sprite file (in the case of icons, they can be in an SVG sprite image).
* [ ] **Width and Height:** ![High][high_img] All `<img>` have height and width set (Don't specify px or %).

> ***Note:*** Lots of developers assume that width and height are not compatible with responsive web design. It's absolutely not the case.

* [ ] **Alternative text:** ![High][high_img] All `<img>` have an alternative text which describe the image visually.
* [ ] **Lazy loading:** ![Medium][medium_img] Images are lazyloaded (A noscript fallback is always provided).

**[⬆ back to top](#table-of-contents)**

---

## JavaScript

### Best practices

* [ ] **JavaScript Inline:** ![High][high_img] You don't have any JavaScript code inline (mixed with your HTML code).
* [ ] **Concatenation:** ![High][high_img] JavaScript files are concatenated.
* [ ] **Minification:** ![High][high_img] JavaScript files are minified (you can add the `.min` suffix).

> [Minify Resources (HTML, CSS, and JavaScript)](https://developers.google.com/speed/docs/insights/MinifyResources)

* [ ] **JavaScript security:**

> [Guidelines for Developing Secure Applications Utilizing JavaScript](https://www.owasp.org/index.php/DOM_based_XSS_Prevention_Cheat_Sheet#Guidelines_for_Developing_Secure_Applications_Utilizing_JavaScript)*

* [ ] **Non-blocking:** ![Medium][medium_img] JavaScript files are loaded asynchronously using `async` or deferred using `defer` attribute.

> 📖 [Remove Render-Blocking JavaScript](https://developers.google.com/speed/docs/insights/BlockingJS)

* [ ] **Modernizr:** ![Low][low_img] If you need to target some specific features you can use a custom Modernizr to add classes in your `<html>` tag.

> 🛠 [Customize your Modernizr](https://modernizr.com/download?setclasses)

### JavaScript testing

* [ ] **ESLint:** ![High][high_img] No errors are flagged by ESLint (based on your configuration or standards rules).

> * 📖 [ESLint - The pluggable linting utility for JavaScript and JSX](https://eslint.org/)

**[⬆ back to top](#table-of-contents)**

---

## Security

### Scan and check your web site

> * [securityheaders.io](https://securityheaders.io/)
> * [Observatory by Mozilla](https://observatory.mozilla.org/)
> * [ASafaWeb - Automated Security Analyser for ASP.NET Websites](https://asafaweb.com/)

### Best practices

* [ ] **HTTPS:** ![Medium][medium_img] HTTPS is used on every pages and for all external content (plugins, images...).

> * 🛠 [Let's Encrypt - Free SSL/TLS Certificates](https://letsencrypt.org/)
> * 🛠 [Free SSL Server Test](https://www.ssllabs.com/ssltest/index.html)
> * 📖 [Strict Transport Security](http://caniuse.com/#feat=stricttransportsecurity)

* [ ] **HTTP Strict Transport Security (HSTS):** ![Medium][medium_img] The HTTP header is set to 'Strict-Transport-Security'.

> * 🛠 [Check HSTS preload status and eligibility](https://hstspreload.org/)
> * 📖 [HTTP Strict Transport Security Cheat Sheet - OWASP](https://www.owasp.org/index.php/HTTP_Strict_Transport_Security_Cheat_Sheet)
> * 📖 [Transport Layer Protection Cheat Sheet - OWASP](https://www.owasp.org/index.php/Transport_Layer_Protection_Cheat_Sheet)

* [ ] **Cross Site Request Forgery (CSRF):** ![High][high_img] You are ensure that requests made to your server-side are legitimate and originate from your website / app to prevent CSRF attacks.

> 📖 [Cross-Site Request Forgery (CSRF) Prevention Cheat Sheet  - OWASP](https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF)_Prevention_Cheat_Sheet)

* [ ] **Cross Site Scripting (XSS):** ![High][high_img] Your page or website is free from XSS possible issues.

> * 📖 [XSS (Cross Site Scripting) Prevention Cheat Sheet  - OWASP](https://www.owasp.org/index.php/XSS_(Cross_Site_Scripting)_Prevention_Cheat_Sheet)
> * 📖 [DOM based XSS Prevention Cheat Sheet  - OWASP](https://www.owasp.org/index.php/DOM_based_XSS_Prevention_Cheat_Sheet)

* [ ] **Content Type Options** ![Medium][medium_img] Prevents Google Chrome and Internet Explorer from trying to mime-sniff the content-type of a response away from the one being declared by the server.

> * 📖 [X-Content-Type-Options - Scott Helme](https://scotthelme.co.uk/hardening-your-http-response-headers/#x-content-type-options)

* [ ] **X-Frame-Options (XFO)** ![Medium][medium_img] Protects your visitors against clickjacking attacks.

> * 📖 [X-Frame-Options - Scott Helme](https://scotthelme.co.uk/hardening-your-http-response-headers/#x-frame-options)
> * 📖 [RFC7034 - HTTP Header Field X-Frame-Options](https://tools.ietf.org/html/rfc7034)

**[⬆ back to top](#table-of-contents)**

---

## Performance

### Best practices

- [ ] **Weight page:** ![High][high_img] The weight of each page is between 0 and 500 KB.

> * 🛠 [Website Page Analysis](https://tools.pingdom.com)
> * 📖 [Size Limit: Make the Web lighter](https://evilmartians.com/chronicles/size-limit-make-the-web-lighter)

- [ ] **Minified:** ![Medium][medium_img] Your HTML is minified.
> 🛠 [W3C Validator](https://validator.w3.org/)

* [ ] **Lazy loading:** ![Medium][medium_img] Images, scripts and CSS need to be lazy loaded to improve the response time of the current page (See details in their respective sections).

* [ ] **Cookie size:** If you are using cookies be sure each cookie doesn't exceed 4096 bytes and your domain name don't have more than 20 cookies.

> * 📖 [Cookie specification: RFC 6265](https://tools.ietf.org/html/rfc6265)
> * 📖 [Cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)
> * 🛠 [Browser Cookie Limits](http://browsercookielimits.squawky.net/)

### Performance testing

* [ ] **Google PageSpeed:** ![High][high_img] All your pages were tested (not only the homepage) and have a score of at least 90/100.

> * 🛠 [Google PageSpeed](https://developers.google.com/speed/pagespeed/insights/)
> * 🛠 [Test your mobile speed with Google](https://testmysite.withgoogle.com)
> * 🛠 [WebPagetest - Website Performance and Optimization Test](https://www.webpagetest.org/)

**[⬆ back to top](#table-of-contents)**

---

## Accessibility

> **Notes:** You can watch the playlist [A11ycasts with Rob Dodson](https://www.youtube.com/playlist?list=PLNYkxOF6rcICWx0C9LVWWVqvHlYJyqw7g) 📹

### Best practices

- [ ] **Progressive enhancement:** ![Medium][medium_img] Major functionality like main navigation and search should work without JavaScript enabled.

> 📖 [Enable / Disable JavaScript in Chrome Developer Tools](https://www.youtube.com/watch?v=kBmvq2cE0D8)

- [ ] **Color contrast:** ![Medium][medium_img] Color contrast should at least pass WCAG AA (AAA for mobile).

> 🛠 [Contrast ratio](https://leaverou.github.io/contrast-ratio/)

#### Headings

* [ ] **H1:** ![High][high_img] All pages have an H1 which is not the title of the website.
* [ ] **Headings:** ![High][high_img] Headings should be used properly in the right order (H1 to H6).

> 📹 [Why headings and landmarks are so important -- A11ycasts #18](https://www.youtube.com/watch?v=vAAzdi1xuUY&index=9&list=PLNYkxOF6rcICWx0C9LVWWVqvHlYJyqw7g)

#### Landmarks

- [ ] **Role banner:** ![High][high_img] `<header>` has `role="banner"`.
- [ ] **Role navigation:** ![High][high_img] `<nav>` has `role="navigation"`.
- [ ] **Role main:** ![High][high_img] `<main>` has `role="main"`.

> 📖 [Using ARIA landmarks to identify regions of a page](https://www.w3.org/WAI/GL/wiki/Using_ARIA_landmarks_to_identify_regions_of_a_page)

### Semantics

- [ ] **Specific HTML5 input types are used:** ![Medium][medium_img] This is especially important for mobile devices that show customized keypads and widgets for different types.

> 📖 [Mobile Input Types](http://mobileinputtypes.com/)

### Form

* [ ] **Label:** ![High][high_img] A label is associated with each input form element. In case a label can't be displayed, use `aria-label` instead.

> 📖 [Using the aria-label attribute - MDN](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-label_attribute)

### Accessibility testing

* [ ] **Accessibility standards testing:** ![High][high_img] Use the WAVE tool to test if your page respects the accessibility standards.

> 🛠 [Wave testing](http://wave.webaim.org/)

* [ ] **Keyboard navigation:** ![High][high_img] Test your website using only your keyboard in a previsible order. All interactive elements are reachable and usable.
* [ ] **Screen-reader:** ![Medium][medium_img] All pages were tested in a screen-reader (VoiceOver, ChromeVox, NVDA or Lynx).
* [ ] **Focus style:** ![High][high_img] If the focus is disabled, it is replaced by visible state in CSS.

> 📹 [Managing Focus - A11ycasts #22](https://www.youtube.com/watch?v=srLRSQg6Jgg&index=5&list=PLNYkxOF6rcICWx0C9LVWWVqvHlYJyqw7g)

**[⬆ back to top](#table-of-contents)**

---

## SEO

* [ ] **Google Analytics:** ![High][high_img] Google Analytics is installed and correctly configured.
* [ ] **Headings logic:** ![Medium][medium_img] Heading text helps to understand the content in the current page.
* [ ] **sitemap.xml:** ![High][high_img] A sitemap.xml exists and was submitted to Google Search Console (previously Google Webmaster Tools).
* [ ] **robots.txt:** ![High][high_img] The robots.txt is not blocking webpages.

> * 🛠 Test your robots.txt with [Google Robots Testing Tool](https://www.google.com/webmasters/tools/robots-testing-tool)

* [ ] **Structured Data:** ![High][high_img] Pages using structured data are tested and are without errors. Structured data helps crawlers understand the content in the current page.

> * 📖 [Introduction to Structured Data | Search | Google Developers](https://developers.google.com/search/docs/guides/intro-structured-data)
> * 🛠 Test your page with the [Structured Data Testing Tool](https://developers.google.com/structured-data/testing-tool/)

* [ ] **Sitemap HTML:** ![Medium][medium_img] An HTML sitemap is provided and is accessible via a link in the footer of your website.

> * 📖 [Sitemap guidelines | Google Support](https://support.google.com/webmasters/answer/183668?hl=en)
> * 🛠 [Sitemap generator](https://websiteseochecker.com/html-sitemap-generator/)


**[⬆ back to top](#table-of-contents)**

---

## Contributing

**Open an issue or a pull request to suggest changes or additions.**

### Guide

The **Front-End Checklist** repository consists of two branches:

#### 1. `master`

This branch consists of the `README.md` file that is automatically reflected on the [Front-End Checklist](http://frontendchecklist.com/) website.

#### 2. `develop`

This branch will be used to make some significant changes to the structure, content if needed. It is preferable to use the master branch to fix small errors or add a new item.

### Contributors

Check out all the super awesome [contributors](https://github.com/thedaviddias/frontendchecklist/graphs/contributors).

## Authors

**[David Dias](https://github.com/thedaviddias/Front-End-Checklist)**, **[Geoffrey Signorato](https://github.com/geosenna)**, **[Sandeep Ramgolam](https://twitter.com/__Sun__)** and **[Cédric Poilly](https://github.com/CedricPoilly)**.

## License

[![CC0](https://i.creativecommons.org/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

**[⬆ back to top](#table-of-contents)**

[low_img]: http://res.cloudinary.com/djnyaloac/image/upload/v1508238836/level-checklist-low.png
[medium_img]: http://res.cloudinary.com/djnyaloac/image/upload/v1508238836/level-checklist-medium.png
[high_img]: http://res.cloudinary.com/djnyaloac/image/upload/v1508238836/level-checklist-high.png
