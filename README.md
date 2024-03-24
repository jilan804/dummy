import psycopg2



# Establish a connection
conn = psycopg2.connect(
    dbname="dev",
    user="awsuser",
    password="R!de8u&$b",
    host="redshiftbsample.cwe2fmkiaffc.ap-south-1.redshift.amazonaws.com",
    port=5439
)

#if conn.is_connected():
       # print("Database connected successfully!")
try:
    cur = conn.cursor()
    cur.execute('SELECT * from dev.ridedb_bsample.rb_etl_device_info;')
    result = cur.fetchall()
    for i in result:
        print(i)
except psycopg2.OperationalError:
    pass



conn.close()
