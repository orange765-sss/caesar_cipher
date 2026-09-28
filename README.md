def caesar_cipher(text: str, shift: int, mode: str = "encrypt") -> str:
    alphabet = "абвгдеёжзийклмнопрстуфхцчшщъыьэюя"
    result = []

    if mode == "decrypt":
        shift = -shift

    for char in text.lower():
        if char in alphabet:
            old_index = alphabet.index(char)
            new_index = (old_index + shift) % len(alphabet)
            result.append(alphabet[new_index])
        else:
            result.append(char)

    return "".join(result)


def main():
    print("=== ШИФР ЦЕЗАРЯ ===")
    message = input("Введите сообщение (на русском): ")
    key = int(input("Введите ключ (сдвиг в цифрах): "))

    encrypted = caesar_cipher(message, key, mode="encrypt")
    decrypted = caesar_cipher(encrypted, key, mode="decrypt")

    print(f"\n🔒 Зашифровано: {encrypted}")
    print(f"🔓 Расшифровано обратно: {decrypted}")


if __name__ == "__main__":
    main()
