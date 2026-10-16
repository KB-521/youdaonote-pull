相当于一个容器，放置所有的数据；

创建：

```javascript
import Vuex from 'vuex';
Vue.use(Vuex);
new Vuex.Store({
    state:{
        //数据
    },
    getters:{ 
        //函数,数据改变时自动调用
        //第一个形参state代表数据对象
    },
    mutations:{
        //同步函数,手动设置调用
        //第一个形参state,后续可以传一个值
    },
    actions:{
        //异步函数,第一个形参context,不能直接改变值
    //通过context.commit('mutations同步函数')修改值
    }
})
```

调用：

```javascript
{{data}}
computed: { 
    data(){ //使用计算属性定义,能在数据改变时实时更新
        return this.$store.state.数据名;
    }
}
```

辅组函数：

```javascript
import {mapState,mapGetters,mapActions} from 'vuex'
import {mapMutations,mapActions} from 'vuex'
computed:{
    ...mapState(['count',...])
} //相当于用计算属性调用参数
```

双向数据绑定：

```javascript
<v-model="valueGetters">
computed:｛
    valueGetters:{
        get(){
            return this.$store.getters.valueGetters;
        },
        set(num){
            this.$store.dispatch('actionsValue', num);
        }
    }
}
```

模块化：

```javascript
//可以将各个组件独立出来,
//也可以将联系到一个变量的函数放在一个文件中,用modules调入
```

