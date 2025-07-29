// Google login
const loginWithGoogle = document.getElementById('loginWithGoogle');

loginWithGoogle && loginWithGoogle.addEventListener('click', async () => {
  try {
    const redirectTo =
      window.location.hostname === '127.0.0.1' || window.location.hostname === 'localhost'
        ? 'http://127.0.0.1:5500/post.html'
        : 'https://rabiamuhammadsaleem.github.io/signup/post.html';

    showLoader(); // tumhara custom loader function

    const { error } = await client.auth.signInWithOAuth({
      provider: 'google',
      options: {
        redirectTo: redirectTo,
      },
    });

    if (error) throw error;
  } catch (err) {
    showAlert({
      icon: 'error',
      title: 'Login Failed',
      text: err.message,
    });
  }
});
