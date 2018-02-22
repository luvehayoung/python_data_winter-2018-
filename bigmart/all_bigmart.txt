# coding: utf-8
get_ipython().magic('ls ')
get_ipython().magic('cd pydata-book-2nd-edition/')
get_ipython().magic('ls ')
import numpy as np; import pandas as pd; from pandas import DataFrame, Series;
train = pd.read_csv('Train.csv')
get_ipython().magic('ls ')
get_ipython().magic('cd bigmart/')
get_ipython().magic('ls ')
train = pd.read_csv('Train.csv')
test = pd.read_csv('Test.csv')
train['source'] = 'train'
test['source'] = 'test'
data = pd.concat([train, test],ignore_index=True)
print(train.shape, test.shape, data.shape)
data.apply(lambda x: sum(x.isnull()))
data.describe()
data.apply(lambda x: len(x.unique()))
categorical_columns = [x for x in data.dtypes.index if data.dtypes[x]=='object']
categorical_columns
categorical_columns = [x for x in categorical_columns if x not in ['Item_Identifier','Outlet_Identifier','source']]
categorical_columns
for col in categorical_columns:
    print('\nFrequency of Categories for variable %s'%col)
    print(data[col].value_counts())
    
item_avg_weight = data.pivot_table(values='Item_Weight', index='Item_Identifier')
item_avg_weight
miss_bool = data['Item_Weight'].isnull()
print('Original #missing: %d'%sum(miss_bool))
data.loc[miss_bool,'Item_Weight'] = data.loc[miss_bool,'Item_Identifier'].apply(lambda x: item_avg_weight[x])
data.loc[miss_bool,'Item_Weight'] = data.loc[miss_bool,'Item_Identifier'].apply(lambda x: item_avg_weight.loc[x])
print('Final #missing: %d'%sum(data['Item_Weight']).isnull())
print('Final #missing: %d'%sum(data['Item_Weight'].isnull()))
from scipy.stats import mode
train_one = data[data['source']=='train]
train_one = data[data['source']=='train']
test_one = data[data['source]=='test']
test_one = data[data['source']=='test']
train_one
test_one
numpy.corrcoef(train_one['Item_Visibility'],train_one['Item_Outlet_Sales])
numpy.corrcoef(train_one['Item_Visibility'],train_one['Item_Outlet_Sales'])
income_level = train_one.group('Outlet_Location_Type')
income_level = train_one.groupby('Outlet_Location_Type')
well_being = income_level['Item_Fat_Content'].value_counts()
well_being
well_being_percent = income_level['Item_Fat_Content'].value_counts(normailze=True)
well_being_percent = income_level['Item_Fat_Content'].value_counts(normalize=True)
well_being_percent
data['Item_Fat_Content'].replace(['LF','reg','low fat'],['Low Fat','Regular','Low Fat'])
data['Item_Fat_Content'].replace(['LF','reg','low fat'],['Low Fat','Regular','Low Fat'], inplace=True)
train_one = data[data['source']=='train]
train_one = data[data['source']=='train']
test_one = data[data['source']=='test']
income_level = train_one.groupby('Outlet_Location_Type')
well_being = income_level['Item_Fat_Content'].value_counts()
well_being
well_being = income_level['Item_Fat_Content'].value_counts(normailize=True)
well_being = income_level['Item_Fat_Content'].value_counts(normalize=True)
well_being = income_level['Item_Fat_Content'].value_counts()
well_being_per = income_level['Item_Fat_Content'].value_counts(normalize=True)
well_being_per
get_ipython().magic('sum bigmart.py 0 59')
get_ipython().magic('save bigmart.py 0 59')
get_ipython().magic('ls ')
get_ipython().magic('save bigmart.py 1 59')
get_ipython().magic('save bigmart.py')
get_ipython().magic('save bigmart2.py 1-64')
preferred = income_level['Item_Typm'].value_counts(normalize=True)
preferred = income_level['Item_Type'].value_counts(normalize=True)
preferred
train_one.head()
train_one['Item_Type'].value_counts()
train_one['Item_level'] = train_one['Item_Type']
train_one['Item_level'] = train_one.loc[:,'Item_Type']
train_one.loc[:,'Item_level'] = train_one.loc[:,'Item_Type']
train_one['Item_level']
train_one['Item_Type'].value_counts()
type(train_one['Item_Type'].value_counts())
train_one['Item_level'].replace(train_one['Item_type'].value_counts(),[1,2,3,2,1,2,3,1,2,3,3,2,3,3,3,1],inplace=True)
train_one['Item_level'].replace(train_one['Item_Type'].value_counts(),[1,2,3,2,1,2,3,1,2,3,3,2,3,3,3,1],inplace=True)
train_one['Item_level'].replace(train_one['Item_Type'].value_counts()tolist(),[1,2,3,2,1,2,3,1,2,3,3,2,3,3,3,1],inplace=True)
train_one['Item_level'].replace(train_one['Item_Type'].value_counts().tolist(),[1,2,3,2,1,2,3,1,2,3,3,2,3,3,3,1],inplace=True)
train_one['Item_level']
train_one['Item_level'].replace(train_one['Item_Type'].value_counts().tolist(),[1,2,3,2,1,2,3,1,2,3,3,2,3,3,3,1],inplace=True)
train_one['Item_level'].replace(train_one['Item_level'].value_counts().tolist(),[1,2,3,2,1,2,3,1,2,3,3,2,3,3,3,1],inplace=True)
train_one['Item_level']
train_one['Item_level'].replace([Fruits and Vegetables,  
Snack Foods,           
Household,             
Frozen Foods,          
Dairy,                 
Canned,                
Baking Goods,          
Health and Hygiene,    
Soft Drinks,           
Meat,                  
Breads,                
Hard Drinks,           
Others,                Starchy Foods,         Breakfast,             
Seafood     ],[1,2,3,2,1,2,3,1,2,3,3,2,3,3,3,1],inplace=True)
train_one['Item_level'].replace(['Fruits and Vegetables',  
'Snack Foods',           
'Household',             
'Frozen Foods',          
'Dairy',                 
'Canned',                
'Baking Goods',          
'Health and Hygiene',    
'Soft Drinks',           
'Meat',                  
'Breads',                
'Hard Drinks',           
'Others',                'Starchy Foods',         'Breakfast',             
'Seafood'     ],[1,2,3,2,1,2,3,1,2,3,3,2,3,3,3,1],inplace=True)
train_one['Item_level']
product_level = train_one.groupby('Outlet_Location')
product_level = train_one.groupby('Outlet_Location_Type')
product_level['Item_level']
product_level['Item_level'].all
item_level = product_level['Item_level'].value_counts(normalize=True)
item_level
import matplotlib.pyplot as plt
item_level = item_level.unstack()
item_level
item_level.plot()
product_level = train_one.groupby('Outlet_Location_Type','Item_level')
product_level = train_one.groupby(['Outlet_Location_Type','Item_level'])
item_level = product_level['Item_Outlet_Sales'].sum()
item_level
item_level = product_level['Item_Outlet_Sales'].mean()
item_level
item_level = product_level['Item_Outlet_Sales'].sum()
item_level.plot()
item_level.unstack().plot()
item_level_avg = product_level['Item_Outlet_Sales'].mean()
item_level_avg.unstack().plot()
train_one['Outlet_Location_Type'].value_counts()
get_ipython().magic('save all_bigmart 1-110')
