
# 🧩 JSON to HTML Table Webhook (n8n Workflow)

This n8n workflow sets up a webhook that receives JSON data and responds with a neatly formatted HTML table. It's useful for generating readable reports or displaying structured data directly in the browser or email.

---

## 🚀 How It Works

1. A **Webhook node** listens for incoming `GET` or `POST` requests.
2. A **Function node** processes the incoming JSON and converts it into an HTML `<table>`.
3. The final response is returned as HTML through the Webhook Response.

---

## 📥 Example JSON Input
```json
[
  {
    "title": "Shop for Rent",
    "rahn": "Deposit: 50,000,000 IRR",
    "ejare": "Rent: 5,000,000 IRR",
    "place": "2 hours ago in Tehran"
  },
  ...
]
```

---

## 🧠 Function Node Code (HTML Table Generator)
```javascript
const data = items.map(item => item.json);

let html = '<table border="1" cellpadding="5" cellspacing="0" style="border-collapse: collapse;">';
html += '<tr><th>Title</th><th>Deposit</th><th>Rent</th><th>Location</th></tr>';

data.forEach(row => {
  html += '<tr>';
  html += `<td>${row.title || ''}</td>`;
  html += `<td>${row.rahn || ''}</td>`;
  html += `<td>${row.ejare || ''}</td>`;
  html += `<td>${row.place || ''}</td>`;
  html += '</tr>';
});

html += '</table>';

return [{ json: { html } }];
```

---

## 🌐 Testing the Webhook

- Make sure the workflow is **active** in n8n (not just in "Execute" mode).
- Send a request to your webhook URL, such as:

  ```
  https://your-n8n-instance/webhook/show-table
  ```

- The response will be a full HTML table rendered in your browser.

---

## ✅ Notes

- Works great for integrating with forms, APIs, or scheduled triggers.
- You can further customize the table with CSS, inline styles, or export it to PDF/email.
