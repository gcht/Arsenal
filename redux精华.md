# 1.action -- action.js
```
  const action = {
    type: 'home',
    msg: 'Write Document'
}; 
```
# 2.reducer -- reducer.js
定义：const reducer = function(state, action)
```
  const defalutState = 'home';
  export default (state = defalutState, action) => {
    switch (action.type) {
      case 'HOME':
        return 'home';
      case 'LIST' :
        return 'list';
      case 'SHOPCAR' :
        return 'shopCar';
      case 'MY' :
        return 'my';
      default:
        return state;
    }
  }
```
# 3.creteStore -- store.js
```
  import { createStore } from 'redux';
  import reducer from '../redux/reducer.js';
  export default createStore(reducer);
```
# 4.dispatch -- dispathc.js
```
  import store from './store.js';
  export default (action) => {
    store.dispatch(action);
  };
```

# 5. App
```
  const changeState = (type) => {
    store.dispatch({
      type:type,
      msg:'点击了‘ + type + '菜单’
    });
  };
  class Footer extends React.Component {   
    render() {
      const state = store.getState();
      return (
        <ul className="footer">
          <li><Link className={state == 'home' ? 'active' : ''} to="/" onClick={changeState.bind(this, 'HOME')}>首页</Link></li>
          <li><Link className={state == 'list' ? 'active' : ''} to="/list" onClick={changeState.bind(this, 'LIST')}>分类</Link></li>
          <li><Link className={state == 'shopCar' ? 'active' : ''} to="/shopCar" onClick={changeState.bind(this, 'SHOPCAR')}>购物车</Link></li>
          <li><Link className={state == 'my' ? 'active' : ''} to="/my" onClick={changeState.bind(this, 'MY')}>我的</Link></li>
        </ul>
      );
    }
  }
```
