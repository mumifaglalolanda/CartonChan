Configuración Recomendada para instance-config.php
==================================================

Es importante que tú mismo te familiarices con los archivos de configuración `inc/config.php` e `inc/instance-config.php`,
y descubras todas sus posibilidades. Para ello, lo mejor es ir leyendo poco a poco cada linea de código junto a los comentarios
en `config.php`, e ir incorporandolos a `instance-config.php`, y experimentando con cada variable de configuración. Recuerda que
__no debes modificar bajo ningún motivo__ el archivo `config.php`, que para eso está `instance-config.php`, o se te hará dificil
actualizar tu versión de _Vichan_.

Sin embargo, si careces totalmente de los conocimientos y no tienes tiempo o ganas, aquí te dejo la versión de `instance-config.php`
con la que trabaja _La Sociedad de los Lolchanesmuertos_.

__Nota__: no necesariamente es la configuración más óptima.

```
<?php

/*
*  Instance Configuration
*  ----------------------
*  Edit this file and not config.php for imageboard configuration.
*
*  You can copy values from config.php (defaults) and paste them here.
*/

	$config['php_md5'] = true;

	/* ¡Estos campos los tienes que rellenar tú, de acuerdo a tu servidor y tu base de datos!
		o en el caso de que ya los tengas, no debes modificarlos! */
	$config['db']['server'] = '';
	$config['db']['database'] = '';
	$config['db']['prefix'] = '';
	$config['db']['user'] = '';
	$config['db']['password'] = '';


	$config['cookies']['mod'] = 'mod';
	$config['cookies']['salt'] = 'MmJhMzc2ZTg4MjMzNjE2OTRiMmVjOG';

	$config['flood_time'] = 1;
	$config['flood_time_ip'] = 1;
	$config['flood_time_same'] = 1;
	$config['max_body'] = 1800;
	$config['reply_limit'] = 250;
	$config['max_links'] = 20;
	$config['thumb_width'] = 255;
	$config['thumb_height'] = 255;
	$config['threads_per_page'] = 10;
	$config['max_pages'] = 20;
	$config['threads_preview'] = 5;
	$config['root'] = '';	/** Este campo debes conservarlo de acuerdo a como lo tenías en un inicio. Es "/" si deseas que la raíz de tu imageboard sea htdocs o public_html o es "/titulo/" si la raíz es "htdocs/titulo" ó "public_html/titulo" **/
	$config['secure_trip_salt'] = 'MmU2OWQyNWYwZjIwNzE0YTdkNzc1OD';


	$config['debug'] = false;
	$config['debug_explain'] = false;
	$config['verbose_errors'] = true;




/*
 * ====================
 *  Flood/spam settings
 * ====================
 */

	// Enable reCaptcha to make spam even harder. Rarely necessary.
	$config['recaptcha'] = false;

	// Minimum time between between each post by the same IP address.
	$config['flood_time'] = 10;
	// Minimum time between between each post with the exact same content AND same IP address.
	$config['flood_time_ip'] = 120;
	// Same as above but by a different IP address. (Same content, not necessarily same IP address.)
	$config['flood_time_same'] = 30;

/*
 * ====================
 *  Post settings
 * ====================
 */

	// Do you need a body for new threads?
	$config['force_body_op'] = false;

	// Maximum post body length.
	$config['max_body'] = 8000;

	// Allow users to mark their image as a "spoiler" when posting. The thumbnail will be replaced with a
	// static spoiler image instead (see $config['spoiler_image']).
	$config['spoiler_images'] = true;

	// Allow "uploading" images via URL as well. Users can enter the URL of the image and then Tinyboard will
	// download it. Not usually recommended.
	$config['allow_upload_by_url'] = true;
	// The timeout for the above, in seconds.
	$config['upload_by_url_timeout'] = 1000;
	
	// Example: Custom tripcodes. The below example makes a tripcode of "#test123" evaluate to "!HelloWorld".
	// Example: Custom secure tripcode.
	//$config['custom_tripcode']['##securetrip'] = '!!somethingelse';
	
	

	// Use semantic URLs for threads, like /b/res/12345/daily-programming-thread.html
	$config['slugify'] = true;
	
	// Max size for slugs
	$config['slug_max_size'] = 80;
	
/*
* ====================
*  Ban settings
* ====================
*/

	// Show the post the user was banned for on the "You are banned" page.
	$config['ban_show_post'] = true;

/*
 * ====================
 *  Markup settings
 * ====================
 */
	
	// "Wiki" markup syntax ($config['wiki_markup'] in pervious versions):
	
	/** Puedes establecer la ruta que desees para el archivo, y deberás subir el archivo a dicha ruta para que funcione, obviamente! **/
	$config['markup'][] = array('*:v*', '<img src="'.$config['root'].'/img/smileys/pacman.png" alt=":v" title="Pacman">');
	
	// Symbols
	$config['markup'][] = array("/'''(.+?)'''/", "<strong>\$1</strong>");
	$config['markup'][] = array("/''(.+?)''/", "<em>\$1</em>");
	$config['markup'][] = array("/__(.+?)__/", "<u>\$1</u>");
	$config['markup'][] = array("/~~(.+?)~~/", "<strike>\$1</strike>");
	$config['markup'][] = array("/\*\*(.+?)\*\*/", "<span class=\"spoiler\">\$1</span>");
	$config['markup'][] = array("/^[ |\t]*==(.+?)==[ |\t]*$/m", "<span class=\"heading\">\$1</span>");
	$config['markup'][] = array("/\^\^\^(.+?)\^\^\^/", "<span class=\"smooth-blink\">\$1</span>");
	$config['markup'][] = array("/\^\^(.+?)\^\^/", "<span class=\"blink\">\$1</span>");
	$config['markup'][] = array("/^&lt;(.+?)$/m", "<span class=\"quote-alt\">&lt;\$1</span>");
	$config['markup'][] = array("/\(\(\((.+?)\)\)\)/", "<span class=\"blue-text\">(((\$1)))</span>");
	
	// BBCodes
	$config['markup'][] = array("/\[b\](.+?)\[\/b\]/", "<strong>\$1</strong>");
	$config['markup'][] = array("/\[i\](.+?)\[\/i\]/", "<em>\$1</em>");
	$config['markup'][] = array("/\[u\](.+?)\[\/u\]/", "<u>\$1</u>");
	$config['markup'][] = array("/\[s\](.+?)\[\/s\]/", "<strike>\$1</strike>");
	$config['markup'][] = array("/\[spoiler\](.+?)\[\/spoiler\]/", "<span class=\"spoiler\">\$1</span>");
	$config['markup'][] = array("/\[blink\](.+?)\[\/blink\]/", "<span class=\"blink\">\$1</span>");
	$config['markup'][] = array("/\[sblink\](.+?)\[\/sblink\]/", "<span class=\"smooth-blink\">\$1</span>");

/*
 * ====================
 *  Image settings
 * ====================
 */

	// Maximum image upload size in bytes.
	$config['max_filesize'] = 10 * 1024 * 1024; // 10MB
	// Maximum image dimensions.
	$config['max_width'] = 10000;
	$config['max_height'] = $config['max_width'];

	// Allowed additional file extensions (not images; downloadable files).
	$config['allowed_ext_files'][] = 'swf';

	// Thumbnail to use for the non-image file uploads.
	$config['file_icons']['swf'] = 'swf.png';

/*
 * ====================
 *  Board settings
 * ====================
 */

	// The default name (ie. Anonymous). Can be an array - in that case it's picked randomly from the array.
	// Example: $config['anonymous'] = array('Bernd', 'Senpai', 'Jonne', 'ChanPro');
	// $config['anonymous'] = 'Anonymous';

/*
 * ====================
 *  Webm settings
 * ====================
 */


	//webm
	$config['allowed_ext_files'][] = 'webm';
	$config['webm']['allow_audio'] = true;
	$config['webm']['max_length'] = 5000;

/*
$config['webm']['use_ffmpeg'] = true;

// If your ffmpeg binary isn't in your path you need to set these options
// as well.

$config['webm']['ffmpeg_path'] = '/path/to/ffmeg';
$config['webm']['ffprobe_path'] = '/path/to/ffprobe';
*/


/*
 * ====================
 *  Display settings
 * ====================
 */

	// Tinyboard has been translated into a few langauges. See inc/locale for available translations.
	$config['locale'] = 'en'; // (en, ru_RU.UTF-8, fi_FI.UTF-8, pl_PL.UTF-8)

	// Timezone to use for displaying dates/tiems.
	$config['timezone'] = 'America/La_Paz';
	// The format string passed to strftime() for displaying dates.
	// http://www.php.net/manual/en/function.strftime.php
	$config['post_date'] = '%d/%b/%Y (%a) %I:%M %p';
	// Same as above, but used for "you are banned' pages.
	$config['ban_date'] = '%A %e %B, %Y';
	
	// The names on the post buttons. (On most imageboards, these are both just "Post").
	$config['button_newtopic'] = _('Nuevo Hilo');
	$config['button_reply'] = _('Responder');
		
	// Additional lines added to the footer of all pages.
	$config['footer'][] = _('Copyright © '.date('Y').' La Sociedad de los Lolchanesmuertos.'); // Cambia ésto a tu gusto.
	
	// Optional banner image at the top of every page.
	$config['url_banner'] = $config['root'] . 'banner.php';
	// Banner dimensions are also optional. As the banner loads after the rest of the page, everything may be
	// shifted down a few pixels when it does. Making the banner a fixed size will prevent this.
	$config['banner_width'] = 340;
	$config['banner_height'] = 120;
	
	$config['banners_folder'] = 'img/banners/';		// la ruta relativa a la carpeta donde están tus banners
	
	$config['banners'] = array();
	
	// Agrega cuantos banners desees
	$config['banners'][] = "filename.fileextension";
	$config['banners'][] = "my-banner.jpg";

	// Custom stylesheets available for the user to choose. See the "stylesheets/" folder for a list of
	// available stylesheets (or create your own).
	$config['stylesheets']['Yotsuba B'] = ''; // Default; there is no additional/custom stylesheet for this.
	$config['stylesheets']['Yotsuba'] = 'yotsuba.css';
	/*$config['stylesheets']['Futaba'] = 'futaba.css';
	$config['stylesheets']['Dark'] = 'dark.css';
	$config['stylesheets']['Burichan'] = 'burichan.css';
	$config['stylesheets']['Caffe'] = 'caffe.css';
	$config['stylesheets']['Confraria'] = 'confraria.css';
	$config['stylesheets']['Confraria'] = 'confraria.css';
	$config['stylesheets']['Dark Roach'] = 'dark_roach.css';
	$config['stylesheets']['Favela'] = 'favela.css';
	$config['stylesheets']['Ferus'] = 'ferus.css';
	$config['stylesheets']['Futaba+Vichan'] = 'futaba+vichan.css';
	$config['stylesheets']['Futaba Light'] = 'futaba-light.css';
	$config['stylesheets']['gentoochan'] = 'gentoochan.css';
	$config['stylesheets']['greendark'] = 'greendark.css';
	$config['stylesheets']['Jungle'] = 'jungle.css';
	$config['stylesheets']['Luna'] = 'luna.css';
	$config['stylesheets']['Miku'] = 'miku.css';
	$config['stylesheets']['Nigrachan'] = 'nigrachan.css';
	$config['stylesheets']['Northboard Cb'] = 'northboard_cb.css';
	$config['stylesheets']['Notsuba'] = 'notsuba.css';
	$config['stylesheets']['Novo Jungle'] = 'novo_jungle.css';
	$config['stylesheets']['Photon'] = 'photon.css';
	$config['stylesheets']['Piwnichan'] = 'piwnichan.css';
	$config['stylesheets']['Ricechan'] = 'ricechan.css';
	$config['stylesheets']['Roach'] = 'roach.css';
	$config['stylesheets']['Rugby'] = 'rugby.css';
	$config['stylesheets']['Sharp'] = 'sharp.css';
	$config['stylesheets']['Stripes'] = 'stripes.css';
	$config['stylesheets']['Szalet'] = 'szalet.css';
	$config['stylesheets']['Terminal2'] = 'terminal2.css';
	$config['stylesheets']['TestOrange'] = 'testorange.css';
	$config['stylesheets']['V8ch'] = 'v8ch.css';
	$config['stylesheets']['Wasabi'] = 'wasabi.css';*/
	
	// The default stylesheet to use.
	$config['default_stylesheet'] = array('Yotsuba B', $config['stylesheets']['Yotsuba B']);

	// Make stylesheet selections board-specific.
	$config['stylesheets_board'] = true;
	
	/*
	 * For lack of a better name, “boardlinks” are those sets of navigational links that appear at the top
	 * and bottom of board pages. They can be a list of links to boards and/or other pages such as status
	 * blogs and social network profiles/pages.
	 *
	 * "Groups" in the boardlinks are marked with square brackets. Tinyboard allows for infinite recursion
	 * with groups. Each array() in $config['boards'] represents a new square bracket group.
	 */

	
	/** Opcional: debes modificarlo de acuerdo a tus necesidades **/
	/*$config['boards'] = array(
		array('home' => $config['root']),
		array('a', 'b', 'c', 'd', 'e'),
		array('n', 'p', 'x', 'h', 'l'),
		array(
			'recent' => $config['root'] . 'recent.html',
			'mod' => $config['root'] . 'mod.php'
		)
	);*/

	// Show "Catalog" link in page navigation. Use with the Catalog theme.
	$config['catalog_link'] = 'catalog.html';


/*
 * ====================
 *  Javascript
 * ====================
 */

	// Some scripts require jQuery. Check the comments in script files to see what's needed. When enabling
	// jQuery, you should first empty the array so that "js/query.min.js" can be the first, and then re-add
	// "js/inline-expanding.js" or else the inline-expanding script might not interact properly with other
	// scripts.
	$config['additional_javascript'] = array();

	/** Todo nuevo javascript que desees integrar a tus boards debe ir aquí **/
	
	$config['api']['enabled'] = true;

	$config['additional_javascript'][] = 'js/jquery.min.js';
	$config['additional_javascript'][] = 'js/strftime.min.js';
	$config['additional_javascript'][] = 'js/jquery.mixitup.min.js';
	$config['additional_javascript'][] = 'js/jquery-ui.custom.min.js';
	$config['additional_javascript'][] = 'js/ajax.js';
	$config['additional_javascript'][] = 'js/ajax-post-controls.js';
	$config['additional_javascript'][] = 'js/auto-reload.js';
	//$config['additional_javascript'][] = 'js/catalog.js';
	$config['additional_javascript'][] = 'js/catalog-link.js';
	$config['additional_javascript'][] = 'js/catalog-search.js';
	$config['additional_javascript'][] = 'js/download-original.js';
	$config['additional_javascript'][] = 'js/expand.js';
	//$config['additional_javascript'][] = 'js/expand-all-images.js';
	$config['additional_javascript'][] = 'js/expand-too-long.js';
	$config['additional_javascript'][] = 'js/expand-video.js';
	//$config['additional_javascript'][] = 'js/favorites.js'; // may conflict with watch.js and compact-boardlist.js
	$config['additional_javascript'][] = 'js/file-selector.js';
	$config['additional_javascript'][] = 'js/fix-report-delete-submit.js';
	//$config['additional_javascript'][] = 'js/forced-anon.js';
	//$config['additional_javascript'][] = 'js/gallery-view.js';
	//$config['additional_javascript'][] = 'js/hide-images.js';  // happy-chon ya tiene su propio "modo seguro"
	$config['additional_javascript'][] = 'js/hide-threads.js';
	//$config['additional_javascript'][] = 'js/id_colors.js';
	//$config['additional_javascript'][] = 'js/id_highlighter.js';
	$config['additional_javascript'][] = 'js/infinite-scroll.js';
	//$config['additional_javascript'][] = 'js/inline.js';
	//$config['additional_javascript'][] = 'js/inline-expanding.js';	// Conflicto con happy-chon
	//$config['additional_javascript'][] = 'js/inline-expanding-filename.js';	// Conflicto con happy-chon
	//$config['additional_javascript'][] = 'js/live-index.js';	// Conflicto con happy-chon
	//$config['additional_javascript'][] = 'js/local-time.js';
	//$config['additional_javascript'][] = 'js/mobile-style.js';	// LATER
	//$config['additional_javascript'][] = 'js/compact-boardlist.js';
	//$config['additional_javascript'][] = 'js/watch.js';	// Conflicto con happy-chon
	//$config['additional_javascript'][] = 'js/multi-image.js';
	
	//$config['additional_javascript'][] = 'js/options.js';	// LATER
	//$config['additional_javascript'][] = 'js/style-select.js';	// LATER
	//$config['additional_javascript'][] = 'js/options/general.js';
	//$config['additional_javascript'][] = 'js/no-animated-gif.js';
	//$config['additional_javascript'][] = 'js/options/user-css.js';
	//$config['additional_javascript'][] = 'js/options/user-js.js';
	
	//$config['additional_javascript'][] = 'js/own-board.js'; // still on developement
	$config['additional_javascript'][] = 'js/post-hover.js';
	$config['additional_javascript'][] = 'js/quick-post-controls.js';
	$config['additional_javascript'][] = 'js/quick-reply.js';
	//$config['additional_javascript'][] = 'js/quote-selection.js';
	//$config['additional_javascript'][] = 'js/save-user_flag.js';
	//$config['additional_javascript'][] = 'js/instance.settings.js';
	//$config['additional_javascript'][] = 'js/show-backlinks.js';	// Conflicto con happy-chon
	$config['additional_javascript'][] = 'js/show-op.js';
	$config['additional_javascript'][] = 'js/show-own-posts.js';
	//$config['additional_javascript'][] = 'js/smartphone-spoiler.js';
	//$config['additional_javascript'][] = 'js/threadscroll.js';
	//$config['additional_javascript'][] = 'js/thread-stats.js';
	//$config['additional_javascript'][] = 'js/thread-watcher.js';
	//$config['additional_javascript'][] = 'js/titlebar-notifications.js';
	//$config['additional_javascript'][] = 'js/toggle-images.js'; // Adds a "Hide all images" in top of page under form
	//$config['additional_javascript'][] = 'js/toggle-locked-threads.js';
	//$config['additional_javascript'][] = 'js/treeview.js';
	$config['additional_javascript'][] = 'js/upload-selection.js';
	$config['additional_javascript'][] = 'js/webm-settings.js';
	$config['additional_javascript'][] = 'js/wPaint/8ch.js';
	$config['additional_javascript'][] = 'js/wpaint.js';
	$config['additional_javascript'][] = 'js/ytlinks.js'; // Conflicto con youtube.js - ytlinks.js es mejor
	
	$config['additional_javascript'][] = 'js/cartonchan.js';
	$config['additional_javascript'][] = 'js/happy-chon.js';
	
	//$config['additional_javascript'][] = 'js/shinku.js';
	
/*
 * ====================
 *  Video embedding
 * ====================
 */

	// Enable embedding (see below).
	$config['enable_embedding'] = true;

	// Custom embedding (YouTube, vimeo, etc.)
	// It's very important that you match the entire input (with ^ and $) or things will not work correctly.
	$config['embedding'] = array(
		array(
			'/^https?:\/\/(\w+\.)?youtube\.com\/watch\?v=([a-zA-Z0-9\-_]{10,11})(&.+)?$/i',
			'<p class="fileinfo ytinfo"><a href="https://www.youtube.com/watch?v=$2" target="_blank">Enlace a YouTube</a></p>
			<div class="video-container" data-servicio="youtube" data-video="$2">
				<a href="https://www.youtube.com/watch?v=$2" target="_blank" class="file">
					<img style="max-width:%%tb_width%%px" src="//img.youtube.com/vi/$2/0.jpg" class="post-image">
				</a>
			</div>'
		),
		array(
			'/^https?:\/\/(\w+\.)?vimeo\.com\/(\d{2,10})(\?.+)?$/i',
			'<object style="float: left;margin: 10px 20px;" width="%%tb_width%%" height="%%tb_height%%"><param name="allowfullscreen" value="true" /><param name="allowscriptaccess" value="always" /><param name="movie" value="http://vimeo.com/moogaloop.swf?clip_id=$2&amp;server=vimeo.com&amp;show_title=0&amp;show_byline=0&amp;show_portrait=0&amp;color=00adef&amp;fullscreen=1&amp;autoplay=0&amp;loop=0" /><embed src="http://vimeo.com/moogaloop.swf?clip_id=$2&amp;server=vimeo.com&amp;show_title=0&amp;show_byline=0&amp;show_portrait=0&amp;color=00adef&amp;fullscreen=1&amp;autoplay=0&amp;loop=0" type="application/x-shockwave-flash" allowfullscreen="true" allowscriptaccess="always" width="%%tb_width%%" height="%%tb_height%%"></object>'
		),
		array(
			'/^https?:\/\/(\w+\.)?dailymotion\.com\/video\/([a-zA-Z0-9]{2,10})(_.+)?$/i',
			'<object style="float: left;margin: 10px 20px;" width="%%tb_width%%" height="%%tb_height%%"><param name="movie" value="http://www.dailymotion.com/swf/video/$2"><param name="allowFullScreen" value="true"><param name="allowScriptAccess" value="always"><param name="wmode" value="transparent"><embed type="application/x-shockwave-flash" src="http://www.dailymotion.com/swf/video/$2" width="%%tb_width%%" height="%%tb_height%%" wmode="transparent" allowfullscreen="true" allowscriptaccess="always"></object>'
		),
		array(
			'/^https?:\/\/(\w+\.)?metacafe\.com\/watch\/(\d+)\/([a-zA-Z0-9_\-.]+)\/(\?.+)?$/i',
			'<div style="float:left;margin:10px 20px;width:%%tb_width%%px;height:%%tb_height%%px"><embed flashVars="playerVars=showStats=no|autoPlay=no" src="http://www.metacafe.com/fplayer/$2/$3.swf" width="%%tb_width%%" height="%%tb_height%%" wmode="transparent" allowFullScreen="true" allowScriptAccess="always" name="Metacafe_$2" pluginspage="http://www.macromedia.com/go/getflashplayer" type="application/x-shockwave-flash"></div>'
		),
		array(
			'/^https?:\/\/video\.google\.com\/videoplay\?docid=(\d+)([&#](.+)?)?$/i',
			'<embed src="http://video.google.com/googleplayer.swf?docid=$1&hl=en&fs=true" style="width:%%tb_width%%px;height:%%tb_height%%px;float:left;margin:10px 20px" allowFullScreen="true" allowScriptAccess="always" type="application/x-shockwave-flash"></embed>'
		),
		array(
			'/^https?:\/\/(\w+\.)?vocaroo\.com\/i\/([a-zA-Z0-9]{2,15})$/i',
			'<object style="float: left;margin: 10px 20px;" width="148" height="44"><param name="movie" value="http://vocaroo.com/player.swf?playMediaID=$2&autoplay=0"><param name="wmode" value="transparent"><embed src="http://vocaroo.com/player.swf?playMediaID=$2&autoplay=0" width="148" height="44" wmode="transparent" type="application/x-shockwave-flash"></object>'
		)
	);

/*
 * ====================
 *  Mod settings
 * ====================
 */

	// Enable the moving of single replies
	$config['move_replies'] = false;

/*
 * ====================
 *  Mod permissions
 * ====================
 */

	// "Move" a thread to another board (EXPERIMENTAL; has some known bugs)
	$config['mod']['move'] = ADMIN;
	
	
	
/*
 * ====================
 *  Juguetes de email
 * ====================
 */

	/***
	Personaliza aquí todo lo relacionado a los juguetes de email
	ésto no viene por defecto en vichan, ha sido agregado en esta modificación
	***/
	
	$config['toys']['sage']			= 'Sageru';
	$config['toys']['noko']			= 'Noko';
	$config['toys']['#creditos']	= 'Dar Créditos';
	$config['toys']['#qcreditos']	= 'Quitar Créditos';
	$config['toys']['#ruleta']		= 'Ruleta';
	$config['toys']['#dados2']		= 'Dados de 2 Caras';
	$config['toys']['#dados6']		= 'Dados de 6 Caras';
	$config['toys']['#dados10']		= 'Dados de 10 Caras';
	$config['toys']['#dados20']		= 'Dados de 20 Caras';
	$config['toys']['#dados100']	= 'Dados de 100 Caras';
	$config['toys']['#dados999']	= 'Dados de 999 Caras';
	$config['toys']['#fortuna']		= 'Fortuna';
	$config['toys']['#namefag']		= 'Namefag';
	$config['toys']['#waifu']		= 'Asignador de Waifus';
	
	/***Dados***/
	$config['dados'] = '<span class="%s">Haz tirado un dado de %s caras, salió:</span>
		<span class="%s-result">%s</span><br /><br />';
	
	/***Moneda***/
	$config['moneda'] = '<span class="%s">Haz arrojado una moneda, salió:</span>
		<span class="%s-result">'.(rand(0,1)?'cara':'cruz').'</span><br /><br />';
	
	/***Ruleta***/
	// Tiempo que dura el ban cuando te disparas
	// Ejemplos de Formato: 1y, 10d10h10m10s, 30d, 2h30m, 1m30s, 1s
	$config['ruleta']['ban']['time'] = "10m";
	
	// Activar la opción "siempre darse un tiro", solo para debuggear
	$config['ruleta']['ban']['always'] = true;
	
	$config['ruleta']['mensajes'] = array();
	
	// El mensaje que aparece cuando te das un tiro
	// (configura tantos como desees y será mostrado uno de éstos de forma aleatoria).
	$config['ruleta']['mensajes'][] = "BANG! El usuario se pegó un fuzcaso!";
	$config['ruleta']['mensajes'][] = "BANG! El usuario se dió un tiro!";
	$config['ruleta']['mensajes'][] = "BANG! El usuario se voló la cien de un tiro!";
	$config['ruleta']['mensajes'][] = "BANG! El usuario se voló la tapa de los sesos!";

	// El mensaje que aparece cuando fallas
	$config['ruleta']['default'] = '*click*';
	
	$config['ruleta']['body1'] = '<span class="ruleta">Ruleta</span>:';
	$config['ruleta']['body2'] = '<span class="fuscazo">%s</span>';
	
	// El mensaje que aparece en la pantalla de Ban cuando te das un tiro
	$config['ruleta']['ban']['mensajes'] = array();
	
	$config['ruleta']['ban']['mensajes'][] = "¡Te volaste la tapa de los sesos jugando a la ruleta! ¿Ahora quién va a limpiar ese desastre? Tú no, definitivamente...";
	$config['ruleta']['ban']['mensajes'][] = "¡Te diste un fuscazo pero si bien dado!";
	$config['ruleta']['ban']['mensajes'][] = "¡Te pegaste un pepazo en la cien por andar jugando a la fusca cabrón!";
	$config['ruleta']['ban']['mensajes'][] = "¡Te diste un tiro creyendo que jugar a la ruleta rusa no haría daño!";
	$config['ruleta']['ban']['mensajes'][] = "¡Jugando a la fusca dejaste todos tus sesos desparramados por todo el chan!";
	
	/***Créditos***/
	// Agrega tantos tipos de créditos como lo desees, junto con el formato en el que quieres que aparesca
	$config['creditos']['#creditos']		= '<span class="zeebo">Mira vos qué interesante, te dejo</span><span class="zeebo-total">: '.rand(2,1000).' puntines ché!</span>';
	$config['creditos']['#minicreditos']	= '<span class="zeebo">Mira vos qué interesante, te dejo</span><span class="zeebo-total">: 1 puntín!</span>';
	$config['creditos']['#premium']			= '<span class="premium">Mira vos que interesante, te dejo</span><span class="premium-total">: '.rand(2,100).' puntines gold!</span>';
	$config['creditos']['#qcreditos']		= '<span class="qcreditos">No pos qué perrón, te quito</span><span class="qcreditos-total">: '.rand(2,1000).' puntines por pendejo...</span>';
	
	/***Fortunas***/
	$config['fortunas'] = array();
	
	$config['fortunas'][] = 'Coloca tus fortunas aquí.',
	$config['fortunas'][] = '¡Coloca cuantas fortunas quieras!',

	/***Namefag***/
	$g = rand(0,1); // Gender
	
	$config['namefag']['firstname'] = array();
	$config['namefag']['lastname'] = array();
	
	// define tantos "firstname" y "lastname" como quieras
	/** Nota como género masculino siempre aparece en el caso true y el femenino en el caso false (variable $g)
	Puedes ponerlo como quieras pero deberás ser consistente en el orden **/
	
	$config['namefag']['firstname'][] = 'Aspie';
	$config['namefag']['firstname'][] = $g?'Anon':'Femanon';
	
	$config['namefag']['lastname'][] = 'Kawaii!';
	$config['namefag']['lastname'][] = $g?'loleador':'loleadora';



	/***Waifu***/
	// En el %s de $config['waifu']['body'] va $config['waifu']['text'][] y dentro de este último va $config['waifu']['body2']
	$config['waifu']['body'] = '<span class="waifu">Asignador de waifus</span><span class="waifu-result">: %s</span>';
	$config['waifu']['body2'] = '<span><img src="%s"> %s</span>';
	
	$config['waifu']['text'] = array();
	
	$config['waifu']['text'][] = [ 'class' => '',			'msg' => '' ];
	$config['waifu']['text'][] = [ 'class' => '+18 ugly furry goddess',			'msg' => 'Tendrás una noche de pasión con %s.' ];
	
	$config['waifu']['folder'] = 'img/waifus/';
	
	$config['waifu']['options'] = array();
	
	$config['waifu']['options'][] = [ 'img' => 'aisaka.jpg',		'class' => '*',			'name' => 'Aisaka Taiga' ];
```