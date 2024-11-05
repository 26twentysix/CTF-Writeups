# Anti-Spirit FCaptcha

![img.png](task%2Fimg.png)\
Переходим по ссылке https://hackersnhops-fcaptcha.chals.io и начинаем анализировать сайт\
Находим в коде элемента скрипт, который описывает работу капчи, понимаем, что для ее обхода нам нужно поставить галочку в чекбокс и нажать CTRL + F\
```javascript
        const checkboxLabel = document.querySelector('.captcha-text');
        const checkbox = document.getElementById('captchaCheck');
        const tokenInput = document.getElementById('tokenInput');
        const cookieImage = document.getElementById('cookie-image');

        let ctrlKeyHeld = false;
        let checkboxChecked = false;

        checkbox.addEventListener('mouseover', function() {
            if (!checkbox.checked) {
                checkboxLabel.textContent = "I am not human";
            }
        });

        checkbox.addEventListener('mouseout', function() {
            if (!checkbox.checked) {
                checkboxLabel.textContent = "I am human";
            }
        });

        checkbox.addEventListener('change', function() {
            if (checkbox.checked && checkboxLabel.textContent === "I am not human") {
                alert("Since you indicated you are not human, you may not proceed.");
                checkbox.checked = false;
            }
        });

	document.addEventListener('keydown', function(event) {
	    if (event.key === 'Control' || event.key === 'Meta') {
		ctrlKeyHeld = true;
	    }
	    if (ctrlKeyHeld && event.key === 'f') {
		event.preventDefault();
		if (checkbox.checked) {
		    setCaptchaToken('valid_token');
		    window.location.href = '/login'; // Redirect to login page
		}
	    }
	});
        
        document.addEventListener('keyup', function(event) {
            if (event.key === 'Control' || event.key === 'Meta') {
                ctrlKeyHeld = false;
                checkSubmitConditions();
            }
        });

        checkbox.addEventListener('change', function() {
            checkboxChecked = checkbox.checked;
            checkSubmitConditions();
        });

        function checkSubmitConditions() {
            if (ctrlKeyHeld && checkboxChecked) {
                setCaptchaToken('valid_token');
            }
        }

        function setCaptchaToken(token) {
            tokenInput.value = token;
            localStorage.setItem('captchaToken', token);
            document.getElementById('captchaForm').submit();
            showCookieImage();
        }

        function showCookieImage() {
            const storedToken = localStorage.getItem('captchaToken');
            if (storedToken) {
                cookieImage.style.display = 'block';
            }
        }
```
Отправляем в консоль 
```javascript
captchaCheck.checkbox = true
document.dispatchEvent(new KeyboardEvent('keydown', { key: 'Control', ctrlKey: true }));
document.dispatchEvent(new KeyboardEvent('keydown', { key: 'f', ctrlKey: true }));
```
Получаем куки authentication: false, меняем на true, получаем флаг\
