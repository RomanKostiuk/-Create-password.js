const crypto = require('crypto');
const prompt = require('prompt');

prompt.start();

prompt.get(['pass', 'confirmPass'], (err, res) => {
    if (err) {
        console.error('Виникла помилка:', err);
        return;
    }

    const { pass, confirmPass } = res;

    if (pass === confirmPass) {
        const hash = crypto.createHash('sha256').update(pass).digest('hex');
        console.log('Пароль підтверджено та успішно захешовано:');
        console.log(hash);
    } else {
        console.log('Введені паролі різні. Повторіть спробу.');
    }
});
