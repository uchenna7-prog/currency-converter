from flask import Flask, request, jsonify
from flask_mail import Mail, Message
from flask_cors import CORS

app = Flask(__name__)
CORS(app)  # allows your frontend on Vercel to talk to this backend

# 🔧 Configure your email settings
app.config['MAIL_SERVER'] = 'smtp.gmail.com'
app.config['MAIL_PORT'] = 587
app.config['MAIL_USE_TLS'] = True
app.config['MAIL_USERNAME'] = 'your_email@gmail.com'  # replace this
app.config['MAIL_PASSWORD'] = 'your_app_password'      # replace this
app.config['MAIL_DEFAULT_SENDER'] = 'your_email@gmail.com'

mail = Mail(app)

# 📩 Route to handle contact form submission
@app.route('/contact', methods=['POST'])
def contact():
    data = request.get_json()
    name = data.get('name')
    email = data.get('email')
    message = data.get('message')

    # compose the email
    msg = Message(subject=f"New Contact from {name}",
                  recipients=['your_email@gmail.com'],  # where you'll receive it
                  body=f"Name: {name}\nEmail: {email}\n\nMessage:\n{message}")

    try:
        mail.send(msg)
        return jsonify({"success": True, "message": "Email sent successfully!"}), 200
    except Exception as e:
        return jsonify({"success": False, "message": str(e)}), 500


@app.route('/')
def home():
    return "Backend is running!"


if __name__ == '__main__':
    app.run(debug=True)