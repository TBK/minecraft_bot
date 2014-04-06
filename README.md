Thaum the (Minecraft) Bot
=============
https://twitter.com/thaumoctopus

http://www.minecraftforum.net/topic/1119789-164-snakses-mining-bot-v21-for-survival-maps/


-------------------------------
Everything needed to update the bot:
-------------------------------
#1) Decompile MC (client) with MCP.

#2) Add the modifications listed below: 
##net.minecraft.client.network.NetHandlerPlayClient.java
    ```java
    import net.minecraft.client.bot.MinecraftBot;
    
    /** MinecraftBot instance */
    public MinecraftBot mBot;

    public void handleJoinGame(S01PacketJoinGame p_147282_1_)
    {
    (...)
    mBot = new MinecraftBot(this.gameController);
    }
    ```
    
##net.minecraft.client.entity.EntityClientPlayerMP.java
    ```java
    public void onUpdate()
    {
    (...)
    this.sendQueue.mBot.tick();
    }

    public void sendChatMessage(String par1Str)
    {
        if(!this.sendQueue.mBot.chat.isForBot(par1Str)) this.sendQueue.addToSendQueue(new C01PacketChatMessage(par1Str));
    }
    ```

#3) Recompile (with MCP).

#4) Re-Obscure (/MCPxxx/conf/joined.srg - Minecraft v1.7.2) the MC files:
    
    EntityClientPlayerMP.java -> bje.class
    
    NetHandlerPlayClient.java -> biv.class
    
    NetHandlerPlayClient$1.class -> biw.class

#5) Add language strings (.minecraft\assets\virtual\legacy\lang\en_US.lang):
	```text
    key.categories.bot=Bot
    key.botModeDemolisher=Demolisher
    key.botModeWoodcutter=Woodcutter
    key.botFacing=Facing Status
    key.botPause=Pause
    key.botModes=Modes Menu
    key.botSettings=Settings Menu
    key.botActions=Actions Menu
    key.botStop=Stop
	```