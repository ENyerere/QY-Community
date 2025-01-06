<template>
	<view class="chat">
		<div class="chat-messages" ref="messagesContainer">
			<div v-for="(message, index) in messages" :key="index"
				:class="['message', message.fromMe ? 'from-me' : '']">
				<img v-if="!message.fromMe" :src="message.avatar" alt="Avatar" class="avatar" />
				<div class="message-bubble">
					<p>{{ message.text }}</p>
				</div>
				<img v-if="message.fromMe" :src="message.avatar" alt="Avatar" class="avatar avatar-from-me" />
			</div>
		</div>
		<footer class="chat-input">
			<input v-model="newMessage" type="text" placeholder="输入消息..." @keyup.enter="sendMessage" />
			<button class="fs" @click.stop="sendMessage">发送</button>
		</footer>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				newMessage: '',
				messages: [{
						text: '昨天我发现一个小偷，大家晚上注意关好门窗!',
						fromMe: false,
						avatar: '../../../static/业主/yz2.jpg'
					},
					{
						text: '收到',
						fromMe: false,
						avatar: '../../../static/业主/yz4.jpg'
					},
					{
						text: '收到',
						fromMe: false,
						avatar: '../../../static/业主/yz5.jpg'
					},
					{
						text: '收到',
						fromMe: false,
						avatar: '../../../static/业主/yz6.jpg'
					},
					{
						text: '收到',
						fromMe: false,
						avatar: '../../../static/业主/yz1.jpg'
					},
					{
						text: '收到',
						fromMe: false,
						avatar: '../../../static/业主/yz3.jpg'
					}
				],
			};
		},
		methods: {
			sendMessage() {
				if (this.newMessage.trim()) {
					this.messages.push({
						text: this.newMessage.trim(),
						fromMe: true,
						avatar: '../../../static/person/头像0.png',
					});
					this.newMessage = '';
					this.scrollToBottom();
				}
			},
			scrollToBottom() {
				this.$nextTick(() => {
					const container = this.$refs.messagesContainer;
					container.scrollTop = container.scrollHeight;
				});
			},
		},
	};
</script>

<style scoped>
	:root {
		--message-bg: #dcf8c6;
		--input-bg: #f9f9f9;
		--border-color: #ddd;
		--button-bg: #007bff;
		--button-hover-bg: #0056b3;
	}

	.chat {
		display: flex;
		flex-direction: column;
		height: 95vh;
	}

	.chat-messages {
		flex-grow: 1;
		padding: 10px;
		overflow-y: auto;
		border-bottom: 1px solid var(--border-color);
	}

	.message {
		display: flex;
		margin-bottom: 10px;
	}

	.message.from-me {
		justify-content: flex-end;
	}

	.message-bubble {
		max-width: 70%;
		padding: 12px 16px;
		border-radius: 12px;
		background-color: beige;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
		word-break: break-word;
		margin-left: 10px;
		margin-right: 10px;
	}

	.message-bubble p {
		font-size: 20px;
	}

	.avatar {
		width: 40px;
		height: 40px;
		border-radius: 50%;
		margin-right: 10px;
	}

	.message.from-me .avatar {
		margin-left: 10px;
		margin-right: 0;
	}

	.chat-input {
		display: flex;
		padding: 10px;
		background-color: var(--input-bg);
		border-top: 1px solid var(--border-color);
	}

	.chat-input input {
		flex-grow: 1;
		padding: 10px;
		border: 1px solid #ccc;
		border-radius: 4px;
		margin-right: 10px;
	}

	.chat-input button {
		border: none;
		background-color: var(--button-bg);
		border-radius: 4px;
		cursor: pointer;
	}
</style>