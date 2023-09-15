:orphan:

.. currentmodule:: discord

.. _guide_partial_models:

Partial Models
===============

Partial Models are a collection of objects that discord.py offers to assist in performing API requests that normally require full objects to utilise or access.

An example of these would be the :class:`PartialMessage` object. When performing actions on a message, such as :meth:`Message.add_reaction`, you'd normally need to fetch the full :class:`Message` object, which requires an API request.
:class:`PartialMessage` resolves this, as follows:-

.. code-block:: python3
    :linenos:
    :emphasize-lines: 3

    @bot.command()
    async def add_reaction(ctx: commands.Context, *, message_id: int) -> None:
        message = ctx.channel.get_partial_message(message_id)
        await message.add_reaction("\N{THUMBS UP SIGN}")

Line 3 above creates a :class:`PartialMessage` object instead of fetching a full :class:`Message` from the API. We'll go into more detail on this below.
