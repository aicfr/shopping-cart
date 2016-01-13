```
<script>
    var email = document.getElementById('email');
    var password = document.getElementById('password');

    var login = function () {
        if (email.value == 'foo@foo.com' && password.value == 'sa') {
            email.setCustomValidity('');
        } else {
            email.setCustomValidity('Username and/or Password Invalid');
        }
    };

    email.addEventListener('change', login, false);
    password.addEventListener('change', login, false);

    var form = document.getElementById('loginForm');
    form.addEventListener('submit', function () {
        login();
        if (!this.checkValidity()) {
            event.preventDefault();
        }
    }, false);
</script>
```