React-From：

```javascript
import React from "react"

class Form extends React.Component {
  state = {
    fromData: {}
  }

  submitForm = (cb) => {
    cb({ ...this.state.fromData })
  }

  resetForm = () => {
    const { fromData } = this.state
    Object.keys(fromData).forEach(item => {
      fromData[item] = ""
    })

    this.setState({ fromData })
  }

  setValue = (name, value) => {
    this.setState({
      fromData: {
        ...this.state.fromData,
        [name]: value
      }
    })
  }

  render() {
    const { children } = this.props
    const renderChildren = []

    React.Children.forEach(children, (child) => {
      if (child.type.displayName === "fromItem") {
        const { name } = this.props
        const Children = React.cloneElement(child, {
          key: name,
          handleChange: this.setValue,
          value: this.state.fromData[name] || ""
        }, child.props.children)
        renderChildren.push(Children)
      }
    })

    return renderChildren
  }
}

Form.displayName = "form"

function FormItem(props) {
  const { children, name, handleChange, value, label } = props
  const onChange = (value) => {
    handleChange(name, value)
  }

  return (
    <div className="form">
      <span className="label">{label} :</span>
      {
        React.isValidElement(children) && children.type.displayName === "input"
          ? React.cloneElement(children, { onChange, value })
          : null
      }
    </div>
  )
}

FormItem.displayName = "fromItem"


function Input({ onChange, value }) {
  return <input className="input" onChange={e => onChange && onChange(e.target.value)} value={value} />
}
Input.displayName = "input"


export default () => {
  const form = React.useRef(null)

  const submit = () => {
    form.current.submitForm(fromValue => {
      console.log(formValue)
    })
  }

  const reset = () => {
    form.current.resetForm()
  }

  return (
    <div className='box'>

      <Form ref={form} >
        <FormItem name="name" label="我是"  >
          <Input />
        </FormItem>
        <FormItem name="mes" label="我想对大家说"  >
          <Input />
        </FormItem>
        <input placeholder="不需要的input" />
        <Input />
      </Form>

      <div className="btns" >
        <button className="searchbtn" onClick={submit} >提交</button>
        <button className="concellbtn" onClick={reset} >重置</button>
      </div>
    </div>
  )
}
```

