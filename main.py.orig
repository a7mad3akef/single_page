import pymysql
import pymysql.cursors

from flask import Flask, render_template, request, jsonify

# Connect to the database
connection = pymysql.connect(host='sql2.freemysqlhosting.net',
                             user='sql2224070',
                             password='xK3*yF7*',
                             db='sql2224070',
                             cursorclass=pymysql.cursors.DictCursor)

cursor = connection.cursor()
sql = ('select * from tbl_products_info')
cursor.execute(sql)
data = cursor.fetchall()
# print (data)
for item in data:
    print(item['name'])

counter = 0    

# Setting up our web server
app = Flask(__name__, static_url_path='')

@app.route("/")
def hello():
    return render_template('index.html')

@app.route('/change', methods=['GET', 'POST'])
def get_the_data():
    message =  str(request.form['message'])
    global counter
    the_text = data[counter]['name']
    counter += 1
    print(the_text)
    return jsonify({ 'answer':the_text })

if __name__ == "__main__":
    app.run(debug=False)     