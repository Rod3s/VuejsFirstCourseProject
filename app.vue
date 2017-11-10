new Vue({
	el:'#app',
	data:{
		gameOn: false,
		lifeYou: 100,
		lifeMonster: 100,
		logMsgs:[]
	},
	computed:{
		winner:function(){
			console.log('computed');
			if (this.lifeYou < 0 ) {
				alert('you died!');
				this.gameOn=false;
			} else if (this.lifeMonster < 0 ) {
				alert('YOU WIN!');
				this.gameOn=false;}
				;
			return {} 
		}
	},
	methods: {
		Attack:function(){
			youDamage=this.getRandomInt(0,10);
			monsterDamage=this.getRandomInt(0,8);
			this.logMsgs.unshift({
				player:'Player Hits Monster for '+ monsterDamage,
				monster:'Monster Hits Player for '+ youDamage});
			this.lifeYou -= youDamage;
			this.lifeMonster -= monsterDamage;
		},
		SpecialAttack:function(){
			youDamage=this.getRandomInt(0,10);
			monsterDamage=this.getRandomInt(0,28);
			this.logMsgs.unshift({
				player:'Player Hits Monster for '+ monsterDamage,
				monster:'Monster Hits Player for '+ youDamage});
			this.lifeYou -= youDamage;
			this.lifeMonster -= monsterDamage;
		},
		Heal:function(){
			youDamage=this.getRandomInt(0,15);
			this.logMsgs.unshift({
				player:'Player Heals for 10',
				monster:'Monster Hits Player for '+ youDamage});
			this.lifeYou += (10-youDamage);
		},
		StartGame:function(){
			this.gameOn=true;
			this.lifeYou=100;
			this.lifeMonster=100;
			this.logMsgs=[];
		},
		GiveUp:function(){
			this.gameOn=false;
			this.logMsgs=[];
		},
		getRandomInt: function(min, max) {
			min = Math.ceil(min);
			max = Math.floor(max);
			return Math.floor(Math.random() * (max - min)) + min; //The maximum is exclusive and the minimum is inclusive
		}
	}
})