
import asyncio
from aiogram import Bot, Dispatcher
from aiogram.filters import CommandStart
from aiogram.types import Message

TOKEN = "8635542769:AAEcLxlhCf4MbmdI1BilB8nTnw8S1MzlYc8"

dp = Dispatcher()


@dp.message(CommandStart())
async def start_handler(message: Message):
    await message.answer(
        f"Salom, {message.from_user.first_name}! 👋\n"
        "Botimizga xush kelibsiz!"
    )


@dp.message()
async def echo_handler(message: Message):
    await message.answer(message.text or "Xabar qabul qilindi!")


async def main():
    bot = Bot(token=TOKEN)
    try:
        await dp.start_polling(bot)
    finally:
        await bot.session.close()


if __name__ == "__main__":
    asyncio.run(main())
