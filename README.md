# crispy-octo-guacamole
from flask import Flask, render_template, request

app = Flask(__name__)

# Простая база данных товаров
products = [
    {"id": 1, "name": "Ноутбук", "price": 1000},
    {"id": 2, "name": "Смартфон", "price": 500},
    {"id": 3, "name": "Планшет", "price": 800}
]

@app.route('/')
def index():
    return render_template('index.html', products=products)

@app.route('/buy', methods=['POST'])
def buy():
    product_id = int(request.form['product_id'])
    # Здесь можно добавить логику обработки покупки товара
    return f"Вы купили товар с ID {product_id}"

if __name__ == '__main__':
    app.run(debug=True)
