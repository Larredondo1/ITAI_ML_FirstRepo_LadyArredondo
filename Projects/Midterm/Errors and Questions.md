\############Errors I got while working on project and misc questions I prompted####



*###########Below is when I was having trouble the notebook reading the sheet##########*



\---------------------------------------------------------------------------

ModuleNotFoundError                       Traceback (most recent call last)

File c:\\Users\\lulul\\AppData\\Local\\Programs\\Python\\Python313\\Lib\\site-packages\\pandas\\compat\\\_optional.py:158, in import\_optional\_dependency(name, extra, min\_version, errors)

&#x20;   157 try:

\--> 158     module = importlib.import\_module(name)

&#x20;   159 except ImportError as err:



File c:\\Users\\lulul\\AppData\\Local\\Programs\\Python\\Python313\\Lib\\importlib\\\_\_init\_\_.py:88, in import\_module(name, package)

&#x20;    87         level += 1

\---> 88 return \_bootstrap.\_gcd\_import(name\[level:], package, level)



File <frozen importlib.\_bootstrap>:1387, in \_gcd\_import(name, package, level)



File <frozen importlib.\_bootstrap>:1360, in \_find\_and\_load(name, import\_)



File <frozen importlib.\_bootstrap>:1324, in \_find\_and\_load\_unlocked(name, import\_)



ModuleNotFoundError: No module named 'openpyxl'



The above exception was the direct cause of the following exception:



ImportError                               Traceback (most recent call last)

Cell In\[1], line 6

&#x20;     3 import seaborn as sns #for plot

&#x20;     5 # Load the dataset 

\----> 6 df = pd.read\_excel('01 Call-Center-Dataset.xlsx')



File c:\\Users\\lulul\\AppData\\Local\\Programs\\Python\\Python313\\Lib\\site-packages\\pandas\\io\\excel\\\_base.py:481, in read\_excel(io, sheet\_name, header, names, index\_col, usecols, dtype, engine, converters, true\_values, false\_values, skiprows, nrows, na\_values, keep\_default\_na, na\_filter, verbose, parse\_dates, date\_format, thousands, decimal, comment, skipfooter, storage\_options, dtype\_backend, engine\_kwargs)

&#x20;   479 if not isinstance(io, ExcelFile):

&#x20;   480     should\_close = True

\--> 481     io = ExcelFile(

&#x20;   482         io,

&#x20;   483         storage\_options=storage\_options,

&#x20;   484         engine=engine,

&#x20;   485         engine\_kwargs=engine\_kwargs,

&#x20;   486     )

&#x20;   487 elif engine and engine != io.engine:

&#x20;   488     raise ValueError(

&#x20;   489         "Engine should not be specified when passing "

&#x20;   490         "an ExcelFile - ExcelFile already has the engine set"

&#x20;   491     )



File c:\\Users\\lulul\\AppData\\Local\\Programs\\Python\\Python313\\Lib\\site-packages\\pandas\\io\\excel\\\_base.py:1621, in ExcelFile.\_\_init\_\_(self, path\_or\_buffer, engine, storage\_options, engine\_kwargs)

&#x20;  1618 self.engine = engine

&#x20;  1619 self.storage\_options = storage\_options

\-> 1621 self.\_reader = self.\_engines\[engine](

&#x20;  1622     self.\_io,

&#x20;  1623     storage\_options=storage\_options,

&#x20;  1624     engine\_kwargs=engine\_kwargs,

&#x20;  1625 )



File c:\\Users\\lulul\\AppData\\Local\\Programs\\Python\\Python313\\Lib\\site-packages\\pandas\\io\\excel\\\_openpyxl.py:559, in OpenpyxlReader.\_\_init\_\_(self, filepath\_or\_buffer, storage\_options, engine\_kwargs)

&#x20;   541 @doc(storage\_options=\_shared\_docs\["storage\_options"])

&#x20;   542 def \_\_init\_\_(

&#x20;   543     self,

&#x20;  (...)    546     engine\_kwargs: dict | None = None,

&#x20;   547 ) -> None:

&#x20;   548     """

&#x20;   549     Reader using openpyxl engine.

&#x20;   550 

&#x20;  (...)    557         Arbitrary keyword arguments passed to excel engine.

&#x20;   558     """

\--> 559     import\_optional\_dependency("openpyxl")

&#x20;   560     super().\_\_init\_\_(

&#x20;   561         filepath\_or\_buffer,

&#x20;   562         storage\_options=storage\_options,

&#x20;   563         engine\_kwargs=engine\_kwargs,

&#x20;   564     )



File c:\\Users\\lulul\\AppData\\Local\\Programs\\Python\\Python313\\Lib\\site-packages\\pandas\\compat\\\_optional.py:161, in import\_optional\_dependency(name, extra, min\_version, errors)

&#x20;   159 except ImportError as err:

&#x20;   160     if errors == "raise":

\--> 161         raise ImportError(msg) from err

&#x20;   162     return None

&#x20;   164 # Handle submodules: if we have submodule, grab parent module from sys.modules



ImportError: `Import openpyxl` failed.  Use pip or conda to install the openpyxl package.



\###############When I fixed error by installing openpyxl pip install openpyxl#############



\########## Error when checking the data#######

TypeError                                 Traceback (most recent call last)

Cell In\[9], line 13

&#x20;    11 print(df.tail())

&#x20;    12 print("--- Dataset Shape ---")

\---> 13 print(df.shape())

&#x20;    14 print("--- Dataset Info ---")

&#x20;    15 print(df.info())



TypeError: 'tuple' object is not callable



*######### When checking with Claude it was coding error due to it being properties#######*





*####### attempted to do a count plot like in mod 4#####*

df.describe()

df\['Answered (Y/N)'].value\_counts()

plt.figure(figsize=(10, 6))

sns.countplot(x='Y', hue='N', data=df)

plt.title('Calls Answered vs Not Answered')

plt.legend(\['Answered', 'Not Answered'])

plt.show()



NameError                                 Traceback (most recent call last)

Cell In\[3], line 1

\----> 1 df.describe()

&#x20;     2 df\['Answered (Y/N)'].value\_counts()

&#x20;     3 plt.figure(figsize=(10, 6))



NameError: name 'df' is not defined



*########## Used Claude to help fix coding error using it's second suggestion error was in names to the paste###*



\# ❌ Wrong - 'Y' and 'N' are not column names

sns.countplot(x='Y', hue='N', data=df)



\# ✅ Correct - use the actual column name

sns.countplot(x='Answered (Y/N)', data=df)

\########

