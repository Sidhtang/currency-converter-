# currency-converter-

it is a currency converter using API
import requests

def currency_converter(amount, from_currency, to_currency):
    api_key = 'your_exchange_rate_api_key'
    url = f'https://v6.exchangerate-api.com/v6/{api_key}/pair/{from_currency}/{to_currency}/{amount}'

    response = requests.get(url)
    data = response.json()

    if 'error' in data:
        return data['error']

    converted_amount = data['conversion_result']
    return converted_amount

def main():
    amount = float(input("Enter amount to convert: "))
    from_currency = input("Enter from currency (3-letter code, e.g., USD): ").upper()
    to_currency = input("Enter to currency (3-letter code, e.g., EUR): ").upper()

    result = currency_converter(amount, from_currency, to_currency)

    if isinstance(result, str):
        print(f"Error: {result}")
    else:
        print(f"{amount} {from_currency} = {result} {to_currency}")

if __name__ == "__main__":
    main()
