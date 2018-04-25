

-> State is the key that trigger for us and update the ui and it works only for the same component where we want to update the state.

-> We can give the initial value to any state.

-> whatEver value you want to update use the constructor method along with super method and initialize the state, afterthat you need to setUp to set the state.

import React from 'react';
import * as t from 'prop-types';


export class Header extends React.Component{

  constructor(props){
          super();

          this.state = {
            extendDate:props.launch_days,
            status:0
          };

          setTimeout(() => {

            return (this.setState({
                     status:10
                    })
        )}, 2000);

      }
      
      
      extendDate(){
        this.setState({
          extendDate:this.state.extendDate + 5


        });

      }


      


  render(){

      
   let hoby = 'Hobbies';
    return(
        <div>
          
         <h1>Header Goes here</h1>
          
          <div>Site Name:: {this.props.site_name}</div>
          <p>Launch_days:: {this.state.extendDate}</p>
          <p>Status:: {this.state.status}</p>
          <p>Emp Details:: {this.props.employee_details.name}</p>

          <h3>{hoby}</h3>

          <ul>
            hobbies are :

            {this.props.employee_details.hobbies.map((hobby,i) => {
                
                return <li key={i}>{hobby}</li>

            })}
        
          </ul>

          <hr/>

          {this.props.children}

          <hr/>

          <button onClick={this.extendDate.bind(this)} className="btn btn-primary">Extend the launch date</button>

    </div>
    )
  }
}



Header.propTypes = {
site_name: t.string,
launch_days: t.number,
employee_details: t.object,
children: t.element.isRequired
};