# Pandas-Logger
Enables logging of dataframe and series methods

# Example
{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 1,
   "metadata": {},
   "outputs": [],
   "source": [
    "import os\n",
    "os.chdir(\"../..\")\n",
    "import pandas as pd\n",
    "from pandas_logger import logger"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 2,
   "metadata": {},
   "outputs": [],
   "source": [
    "def random_operations(df):\n",
    "    df = df.drop_duplicates()\n",
    "    df = df.drop_duplicates(subset=\"b\")\n",
    "    df = df.merge(df, how=\"outer\", on=\"a\")\n",
    "    df.sort_values(\"a\", inplace=True)\n",
    "    df.dropna(inplace=True)\n",
    "    df = pd.Series([1, 3, 4])\n",
    "    df = df.isnull()\n",
    "    return df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 3,
   "metadata": {},
   "outputs": [
    {
     "name": "stderr",
     "output_type": "stream",
     "text": [
      "2022-01-22 18:41:56,955 - Calling drop_duplicates\n",
      "2022-01-22 18:41:56,956 - Provided Arguments: {}\n",
      "2022-01-22 18:41:56,956 - Initial shape: (3, 2)\n",
      "2022-01-22 18:41:56,959 - Final shape: (3, 2)\n",
      "2022-01-22 18:41:56,960 - Calling drop_duplicates\n",
      "2022-01-22 18:41:56,961 - Provided Arguments: {'subset': 'b'}\n",
      "2022-01-22 18:41:56,961 - Initial shape: (3, 2)\n",
      "2022-01-22 18:41:56,963 - Final shape: (3, 2)\n",
      "2022-01-22 18:41:56,967 - Calling sort_values\n",
      "2022-01-22 18:41:56,968 - Provided Arguments: {'by': 'a', 'inplace': True}\n",
      "2022-01-22 18:41:56,969 - Initial shape: (5, 3)\n",
      "2022-01-22 18:41:56,971 - Final shape: (5, 3)\n",
      "2022-01-22 18:41:56,971 - Calling dropna\n",
      "2022-01-22 18:41:56,972 - Provided Arguments: {'inplace': True}\n",
      "2022-01-22 18:41:56,972 - Initial shape: (5, 3)\n",
      "2022-01-22 18:41:56,977 - Final shape: (2, 3)\n"
     ]
    },
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Enabling Logging\n",
      "0    False\n",
      "1    False\n",
      "2    False\n",
      "dtype: bool\n",
      "Disabling Logging\n",
      "0    False\n",
      "1    False\n",
      "2    False\n",
      "dtype: bool\n"
     ]
    }
   ],
   "source": [
    "print(\"Enabling Logging\")\n",
    "logger.enable_pandas_logging()\n",
    "df = pd.DataFrame([[1, -2], [3, 4], [3, pd.NA]], columns=[\"a\", \"b\"])\n",
    "print(random_operations(df.copy()))\n",
    "print(\"Disabling Logging\")\n",
    "logger.disable_pandas_logging()\n",
    "print(random_operations(df))"
   ]
  }
 ],
 "metadata": {
  "interpreter": {
   "hash": "f80e4ad877d147288d6a0232dc67f959dd1eebc3a7a9a511d90915880cebcace"
  },
  "kernelspec": {
   "display_name": "Python 3.8.5 64-bit ('scraper': conda)",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.8.5"
  },
  "orig_nbformat": 4
 },
 "nbformat": 4,
 "nbformat_minor": 2
}
