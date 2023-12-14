# IMCimport React from 'react';
import {StyleSheet,Text,TextInput,TouchableOpacity,View
} from 'react-native';

export default class App extends React.Component {
  constructor(props){
    super(props)
    this.state = {altura:0,peso:0,resultado:0,resultadoText:""}
    this.calcular = this.calcular.bind(this)
  }
  calcular(){
   let imc = this.state.peso / (this.state.altura * this.state.altura)
   let r = this.state
   r.resultado = imc
   if(r.resultado < 18.5){
     r.resultadoText ='Abaixo do peso'
   }
    else if (r.resultado < 25){
     r.resultadoText ='Normal'
    }
    else if (r.resultado < 30){
     r.resultadoText ='Sobrepeso'
    }
    else if (r.resultado < 40){
     r.resultadoText ='Obesidade' 
    }
    else{
     r.resultadoText ='Obesidade Grave'
    }
   this.setState(r)

  }

  render() {
    return (
      <View style={styles.container}>
        <View style={styles.entrada}>
          <TextInput autoCapitalize="none" placeholder="Altura" keyboardType="numeric" style={styles.input} onChangeText={(altura)=>{this.setState({altura})}}/>
          <TextInput autoCapitalize="none" placeholder="Peso"  keyboardType="numeric" style={styles.input} onChangeText={(peso)=>{this.setState({peso})}}/>
        </View>
        <TouchableOpacity style={styles.button} onPress={this.calcular}><Text style={styles.buttontext}>Calcular</Text></TouchableOpacity>
        <Text style={styles.resultado}>{this.state.resultado.toFixed(2)}</Text>
        <Text style={[styles.resultado,{fontSize:20}]}>{this.state.resultadoText}</Text>

    </View>
    );
  }
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
  },
  entrada:{
    flexDirection:'row',
  },
  input:{
    height:80,
    textAlign:"center",
    width:"50%",
    fontSize:50,
    marginTop:34,
  },
  button:{
   backgroundColor:"#00bfff",
  },
  buttontext:{
    textAlign:"center",
    padding:30,
    fontSize:25,
    fontWeight:'bold',
    color:"white",
  },
  resultado:{
    alignSelf:"center",
    color:"deepskyblue",
    fontSize:45,
    fontWeight:'bold',
    padding: 6,
  },
});

