# react1

React components are of 2 types:
->Function Component
->Class Component

functional component accept props to provide dom

const Button = function(props){
	return (
		<button>{props.label}</button>
	);
};
ReactDOM.render(<Button label="Do"/>, mountNode);


class component accept props and state to provide dom

class Button extends React.Component {
	constructor(props){
		super(props);
		this.state = {counter: 0};
	}

	//state = {counter: 0};

<!-- 	handleClick=()=>{
		this.setState({
			counter: this.state.counter + 1
		})
	}

	handleClick=()=>{
		this.setState((prevState)=>{
			return {
				counter: prevState.counter + 1
			}
		})
	} -->
	handleClick = ()=>{
		this.props.onClick(this.props.incrementValue)
	}
	render(){
		return {
			<button onClick={this.handleClick}>{this.state.counter}</button>
		};
	}
}

const Result = (props)=>{
	return (
		<div>{props.counter}</div>
	);
}
class App extends React.Component{
	state = {counter: 0};

	incrementCounter=(incrementValue)=>{
		this.setState((prevState)=>{
			return {
				counter: prevState.counter + incrementValue
			}
		})
	}
	render(){
		return {
			<Button incrementValue={1} onClick={this.incrementCounter}/>
			<Button incrementValue={2} onClick={this.incrementCounter}/>
			<Button incrementValue={3} onClick={this.incrementCounter}/>
			<Result counter={this.state.counter}/>
		}
	}
}
ReactDOM.render(<App />, mountNode);

props has fixed value can't be changed while state can be changed
class change their internal state not properties


