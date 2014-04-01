Thaum the (Minecraft) Bot
=============
https://twitter.com/thaumoctopus
http://www.minecraftforum.net/topic/1119789-164-snakses-mining-bot-v21-for-survival-maps/

Everything needed to update the bot is to update the sections listed below:

-------------------------------
net.minecraft.client.network.NetHandlerPlayClient.java
-------------------------------
    
    import net.minecraft.client.bot.MinecraftBot;
    
    /** MinecraftBot instance */
    public MinecraftBot mBot;

    public void handleJoinGame(S01PacketJoinGame p_147282_1_)
    {
	(...)
	mBot = new MinecraftBot(this.gameController);
    }
	
	
-------------------------------
net.minecraft.client.entity.EntityClientPlayerMP.java
-------------------------------
    
    public void onUpdate()
    {
	(...)
	this.sendQueue.mBot.tick();
    }

    public void sendChatMessage(String par1Str)
    {
    	if(!this.sendQueue.mBot.chat.isForBot(par1Str)) this.sendQueue.addToSendQueue(new C01PacketChatMessage(par1Str));
    }


-------------------------------
Re-Obscure (/MCPxxx/conf/joined.srg) - Minecraft v1.7.2
-------------------------------
    
    EntityClientPlayerMP.java -> bje.class
	
    NetHandlerPlayClient.java -> biv.class
	
    NetHandlerPlayClient$1.class -> biw.class