# 数据倾斜

import pandas as pd
import random
import string


def generate_userid():
	return ''.join(random.choices(string.digits, k=8))


def generate_order_no():
	return ''.join(random.choices(string.digits, k=10))


def generate_product_no():
	return ''.join(random.choices(string.digits, k=6))


def generate_color_no():
	return ''.join(random.choices(string.digits, k=3))




def generate_sale_amount():
	return round(random.uniform(0, 1000), 2)


# 生成华东地区的数据
data_east = []
for _ in range(80000000):
	data_east.append([
		generate_userid(),
		generate_order_no(),
		"华东",
		generate_product_no(),
		generate_color_no(),
		generate_sale_amount()
	])
df_east = pd.DataFrame(data_east, columns=["userid", "order_no", "region", "product_no", "color_no", "sale_amount"])

# 生成西北地区的数据
data_west = []
for _ in range(20000000):
	data_west.append([
		generate_userid(),
		generate_order_no(),
		"西北",
		generate_product_no(),
		generate_color_no(),
		generate_sale_amount()
	])
df_west = pd.DataFrame(data_west, columns=["userid", "order_no", "region", "product_no", "color_no", "sale_amount"])

# 合并华东和西北的数据
result_df = pd.concat([df_east, df_west], ignore_index=True)
print(result_df)

​    