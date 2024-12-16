const { Client, LocalAuth } = require('whatsapp-web.js');
const qrcode = require('qrcode-terminal');

// Inisialisasi client WhatsApp
const client = new Client({
    authStrategy: new LocalAuth() // Menyimpan sesi login agar tidak perlu scan QR setiap kali
});

// Menampilkan QR Code saat login pertama kali
client.on('qr', (qr) => {
    qrcode.generate(qr, { small: true });
});

// Setelah login berhasil
client.on('ready', () => {
    console.log('Bot sihir siap!');
});

// Menangani pesan masuk dan memberi respons dengan tema fantasi
client.on('message', (message) => {
    console.log(`Pesan dari ${message.from}: ${message.body}`); // Tampilkan pesan di console
    const msg = message.body.toLowerCase();

    // Respons berdasarkan tema fantasi
    if (msg.includes('halo') || msg.includes('hi')) {
        message.reply('Salam, pahlawan! Siapkah kamu untuk petualangan yang penuh misteri?');
    } else if (msg.includes('ramalan')) {
        message.reply('Dalam cermin sihir, aku melihat masa depanmu... sebuah perjalanan besar menanti!');
    } else if (msg.includes('quest')) {
        message.reply('Aku punya quest untukmu: Temui Penyihir Tua di hutan terlarang untuk mendapatkan kekuatan baru!');
    } else if (msg.includes('selamat datang')) {
        message.reply('Selamat datang, petualang! Dunia penuh keajaiban menunggumu!');
    } else if (msg.includes('monster')) {
        message.reply('Hati-hati! Sebuah monster raksasa terlihat di ujung desa, bersiaplah untuk bertempur!');
    } else {
        message.reply('Aku adalah Pemandu Sihir, dan aku selalu siap memberi petunjuk dalam dunia ini.');
    }
});

// Menjalankan bot
client.initialize();

<!---
Tutu1922/Tutu1922 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
