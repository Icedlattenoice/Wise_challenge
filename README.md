# Wise_challenge

$ git clone https://github.com/<Icedlattenoice>/<Wise_challenge>

import matplotlib.pyplot as plt
import numpy as np

account_balance = int(input("What is your account balance?\n"))
my_currency = input("\nWhich currency are you using?\n")
print(f'\nYour account balance is {account_balance} {my_currency} .')

#The client can fill a nested dictionary with their types of spending along with the prices, then we can read the dictionary, take the prices, put them in a list and figure out the total sum by iterating over the list

#After that, we can find the new account balance by subtracting the sum from the previous account balance

my_spendings = {}
print("\nSpending summary: -")
print(my_spendings)

no_of_spendings = input('\nHow many types of spendings were in total?\n')

spending_categories = ['Supermarkets', 'Travel', 'Leisure', 'Shopping', 'Personal finance', 'Personal', 'Transport', 'Bills', 'Cash', 'Cheque', 'Home and property', 'Other']

total_sum = 0
cost_of_payments_array = []
pie_chart_labels = []
total_no_of_transactions = 0

for i in range(int(no_of_spendings)):

    type_of_spending = ''
    type_of_spending = input(f'\nWhat was spending no {i + 1} on?\n')

    my_spendings[type_of_spending] = {}

    # Adding elements one at a time

    for j in range(len(spending_categories)):
        if type_of_spending == spending_categories[j]:
            no_of_transactions = int(input("\nHow many transactions do you have for this type of spending?\n"))
            total_no_of_transactions = total_no_of_transactions + no_of_transactions
            for w in range(no_of_transactions):
                reason_of_payment = input(f"\nWhat was transaction no {w + 1} for?\n")
                pie_chart_labels.append(reason_of_payment)
                cost_of_payment = int(input(f"\nHow much did the transaction no {w + 1} cost?\n"))
                cost_of_payments_array.append(cost_of_payment)
                my_spendings[type_of_spending][reason_of_payment] = cost_of_payment
              
                total_sum = total_sum + cost_of_payment
        else:
          pass
  
print("\nAfter adding the types of spending in the dictionary")
print(f'\nYour spendings are: \n{my_spendings} .')

print(f'\nYou have spent: {total_sum} {my_currency} .')

net_account_balance = account_balance - total_sum

print(f'\nYour net account balance after your spendings is {net_account_balance} {my_currency} .')

if net_account_balance > 0:
  print(f'\nCongratulations! You have {net_account_balance} {my_currency} left. ')
elif net_account_balance == 0:
  print('\nCongratulations! You managed not to exceed your budget!')
else:
  print(f'\nUnfortunately, you have a liability of {net_account_balance} {my_currency} .')

print(f'\nThe cost of payments array is: {cost_of_payments_array} .')
print(f'\nThe pie chart labels array is: {pie_chart_labels} .')
print(total_no_of_transactions)

for z in range(no_of_transactions):
  cost_of_payments_array[z] = (cost_of_payments_array[z] * 100)/total_sum

cost_of_payments_ranked = cost_of_payments_array.copy()
pie_chart_labels_ranked = pie_chart_labels.copy()

cost_of_payments_ranked.sort()
cost_of_payments_ranked.reverse()
pie_chart_labels_ranked.sort()
pie_chart_labels_ranked.reverse()

print('\nBased on the provided data, your top merchants are: ')

if total_no_of_transactions >= 3:
      print(pie_chart_labels_ranked[:3])
else:
  print(pie_chart_labels_ranked)


plt.pie(cost_of_payments_array, labels = pie_chart_labels, autopct='%1.1f%%')
plt.show()


