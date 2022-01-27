- 👋 Hi, I’m @coolhacker123421
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
coolhacker123421/coolhacker123421 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
async function getName() {
    const response = await fetch('https://api.blooket.com/api/users/verify-token', {
        method: "GET",
        headers: {
            "accept": "application/json, text/plain, */*",
            "accept-language": "en-US,en;q=0.9,ru;q=0.8",
        },
        credentials: "include"
    });
    const data = await response.json();

    return data.name;
};

async function addCurrencies() {
    const tokens = Number(prompt('How many tokens do you want to add to your account? (5000 )'));

    if (tokens > 5000) {
        alert('You can only add up to 5000 tokens.');
    };

    const response = await fetch('https://api.blooket.com/api/users/add-rewards', {
        method: "PUT",
        headers: {
            "referer": "https://www.blooket.com/",
            "content-type": "application/json",
        },
        credentials: "include",
        body: JSON.stringify({
            addedTokens: tokens,
            addedXp: 5000,
            name: await getName()
        })
    });

    if (response.status == 200) {
        alert(`${tokens} tokens and 5000 XP added to your account!`);
    } else {
        alert('An error occured.');
    };

};

addCurrencies();
