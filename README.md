# مستندات پلاگین ادیوری برای گودو انجین

زاهنمای پیاده سازی پلاگین ادیوری برای گودو انجین

## دریافت پلاگین
جهت دریافت پلاگین به [این](https://gdpars.sellfile.ir/prod-2174832-%D9%BE%D9%84%D8%A7%DA%AF%DB%8C%D9%86+%D8%AA%D8%A8%D9%84%DB%8C%D8%BA%D8%A7%D8%AA+%D8%AF%D8%B1%D9%88%D9%86+%D8%A8%D8%B1%D9%86%D8%A7%D9%85%D9%87+%D8%A7%DB%8C+%D8%A7%D8%AF%DB%8C%D9%88%D8%B1%DB%8C.html) صفحه مراجه کنید.

## نصب و راه اندازی

ابتدا فایل را از زیپ خارج کرده و بر اساس نسخه گودوی خود فایل ها را در محل پروژه ی خود کپی کنید.

## راه اندازی کتاب‌خانه‌ی ادیوری

ابتدا مطمئن شوید کتاب‌خانه‌ی ادیوری را در `Scene` خود `add_child` کرده‌اید. (فقط گودو 4)

گودو 3:
```gdscript
onready var adivery : Adivery = Adivery.new()
```
گودو 4:
```gdscript
@onready var adivery : Adivery = Adivery.new()

func _ready():
	add_child(adivery)
```
سپس در متد `ready` دستور `configure` را به شکل زیر فرا بخوانید. مقدار `app_id` را با شناسه‌ی اپلیکیشن خود که از داشبورد ناشرین دریافت می‌کنید جایگزین کنید.
```gdscript
func _ready():
	...
	adivery.configure(app_id)
```
## درخواست تبلیغ میان صفحه‌ای
برای درخواست تبلیغ میان ‌صفحه‌ای مشابه نمونه زیر متد `prepare_interstitial_Ad` را صدا بزنید و مقدار `placement_id` را با کلید تبلیغ‌گاه خود که در پنل دریافت می‌کنید، جایگزین کنید.
```gdscript
	adivery.prepare_interstitial_Ad(placement_id)
```
> **هشدار:** <br>
**ادیوری بطور خودکار پس از نمایش یک تبلیغ، تبلیغ بعدی را برای شما آماده می‌کند و نیازی به فراخوانی دوباره دستور فوق ندارید.**

## درخواست تبلیغ جایزه‌ای

برای درخواست تبلیغ جایزه ای مشابه نمونه زیر متد `request_rewarded_ad` را صدا بزنید و مقدار `placement_id` را با کلید تبلیغ‌گاه خود که در پنل دریافت می‌کنید، جایگزین کنید.
```gdscript
	adivery.request_rewarded_ad(placement_id)
```
> **هشدار:** <br>
**ادیوری بطور خودکار پس از نمایش یک تبلیغ، تبلیغ بعدی را برای شما آماده می‌کند و نیازی به فراخوانی دوباره دستور فوق ندارید.**

## درخواست تبلیغ اجرای اپلیکیشن

برای درخواست تبلیغ اجرای اپلیکیشن (AppOpen) مشابه نمونه زیر متد `prepare_app_open_Ad` را صدا بزنید و `placement_id` را با کلید تبلیغ‌گاه خود که از پنل دریافت می‌کنید، جایگزین کنید.
```gdscript
	adivery.prepare_app_open_Ad(placement_id)
```
> **هشدار:** <br>
**ادیوری بطور خودکار پس از نمایش یک تبلیغ، تبلیغ بعدی را برای شما آماده می‌کند و نیازی به فراخوانی دوباره دستور فوق ندارید.**

## اطلاع از وضعیت تبلیغ‌ها
برای اطلاع از وضعیت بارگذاری و یا نمایش تبلیغ‌ها می‌توانید از سیگنال ها کمک بگیرید.

گودو 3:
```gdscript
	adivery.connect("on_app_open_ad_clicked",self,"on_app_open_ad_clicked")
	adivery.connect("on_app_open_ad_closed",self,"on_app_open_ad_closed")
	adivery.connect("on_app_open_ad_loaded",self,"on_app_open_ad_loaded")
	adivery.connect("on_app_open_ad_shown",self,"on_app_open_ad_shown")
	adivery.connect("on_banner_ad_clicked",self,"on_banner_ad_clicked")
	adivery.connect("on_banner_ad_error",self,"on_banner_ad_error")
	adivery.connect("on_banner_ad_loaded",self,"on_banner_ad_loaded")
	adivery.connect("on_interstitial_ad_clicked",self,"on_interstitial_ad_clicked")
	adivery.connect("on_interstitial_ad_closed",self,"on_interstitial_ad_closed")
	adivery.connect("on_interstitial_ad_loaded",self,"on_interstitial_ad_loaded")
	adivery.connect("on_interstitial_ad_shown",self,"on_interstitial_ad_shown")
	adivery.connect("on_rewarded_ad_clicked",self,"on_rewarded_ad_clicked")
	adivery.connect("on_rewarded_ad_closed",self,"on_rewarded_ad_closed")
	adivery.connect("on_rewarded_ad_loaded",self,"on_rewarded_ad_loaded")
	adivery.connect("on_rewarded_ad_shown",self,"on_rewarded_ad_shown")
```
گودو 4:
```gdscript
	adivery.on_app_open_ad_clicked.connect(on_app_open_ad_clicked)
	adivery.on_app_open_ad_closed.connect(on_app_open_ad_closed)
	adivery.on_app_open_ad_loaded.connect(on_app_open_ad_loaded)
	adivery.on_app_open_ad_shown.connect(on_app_open_ad_shown)
	adivery.on_banner_ad_clicked.connect(on_banner_ad_clicked)
	adivery.on_banner_ad_error.connect(on_banner_ad_error)
	adivery.on_banner_ad_loaded.connect(on_banner_ad_loaded)
	adivery.on_interstitial_ad_clicked.connect(on_interstitial_ad_clicked)
	adivery.on_interstitial_ad_closed.connect(on_interstitial_ad_closed)
	adivery.on_interstitial_ad_loaded.connect(on_interstitial_ad_loaded)
	adivery.on_interstitial_ad_shown.connect(on_interstitial_ad_shown)
	adivery.on_rewarded_ad_clicked.connect(on_rewarded_ad_clicked)
	adivery.on_rewarded_ad_closed.connect(on_rewarded_ad_closed)
	adivery.on_rewarded_ad_loaded.connect(on_rewarded_ad_loaded)
	adivery.on_rewarded_ad_shown.connect(on_rewarded_ad_shown)
```
سیگنال ها:
```gdscript
func on_app_open_ad_clicked(placement_id : String):
	#  تبلیغ اجرای اپلیکیشن کلیک شده است. 
	pass

func on_app_open_ad_closed(placement_id : String):
	# تبلیغ اجرای اپلیکیشن بسته شده است. 
	pass

func on_app_open_ad_loaded(placement_id : String):
	# تبلیغ اجرای اپلیکیشن بارگذاری شده است. 
	pass

func on_app_open_ad_shown(placement_id : String):
	# تبلیغ اجرای اپلیکیشن نمایش داده شده است. 
	pass

func on_banner_ad_clicked():
	# تبلیغ بنر کلیک شده است. 
	pass

func on_banner_ad_error(error : String):
	# تبلیغ بنر با خطا مواجه شده است. 
	pass

func on_banner_ad_loaded():
	# تبلیغ بنر بارگذاری شده است. 
	pass

func on_interstitial_ad_clicked(placement_id : String):
	# تبلیغ میان صفحه ای کلیک شده است. 
	pass

func on_interstitial_ad_closed(placement_id : String):
	# تبلیغ میان صفحه ای بسته شده است. 
	pass

func on_interstitial_ad_loaded(placement_id : String):
	# تبلیغ میان صفحه ای بارگذاری شده است. 
	pass

func on_interstitial_ad_shown(placement_id : String):
	# تبلیغ میان صفحه ای نمایش داده شده است. 
	pass

func on_rewarded_ad_clicked(placement_id : String):
	# تبلیغ جایزه ای کلیک شده است. 
	pass

func on_rewarded_ad_closed(placement_id : String, is_rewarded : bool):
	# تبلیغ جایزه ای بسته شده است. 
	# بررسی کنید که آیا کاربر جایزه دریافت می‌کند یا خیر 
	pass

func on_rewarded_ad_loaded(placement_id : String):
	# تبلیغ جایزه ای بارگذاری شده است. 
	pass

func on_rewarded_ad_shown(placement_id : String):
	# تبلیغ جایزه ای نمایش شده است. 
	pass

```
## نمایش تبلیغ
برای نمایش تبلیغ، مشابه زیر متد `show_Ad` را صدا بزنید و `placement_id` تبلیغ‌گاه خود را به عنوان ورودی بدهید.
```gdscript
	adivery.show_add(placement_id)
```
برای نمایش تبلیغ اجرای اپلیکیشن از دستور زیر استفاده کنید.
```gdscript
	adivery.show_app_open_ad(placement_id)
```
> **توجه:** <br>
**برای نمایش تبلیغ های بعدی در اپلیکیشن خود، تنها لازم است تا دستور فوق را دوباره فراخوانی کنید تا تبلیغ نمایش داده شود.**

> **توجه:** <br>
**به دلیل بار‌گذاری مجدد تبلیغات پس از نمایش، از نمایش تبلیغ در تابع های `on_ad_loaded` خودداری کنید.**

×× نمایش تبلیغ بنری
برای نمایش تبلیغ بنری از دستور زیر استفاده کنید.
```gdscript
	adivery.prepare_banner_ad(placement_id, banner_type, position, retry_on_error)
```
جهت پنهان سازی بنر از دستور زیر استفاده کنید.
```gdscript
	adivery.set_banner_visibility(banner_visibility)
```

## نمایش تبلیغ همسان
درحال حاضر این پلاگین از این قابلیت پشتیبانی نمیکند.
