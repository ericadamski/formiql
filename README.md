# formiql
📝 A GraphQL like interface for form generation

```javascript
import gql from 'graphql-tag';
import Formiql from 'formiql';


const typeDefs = [
  gql`
    {
      type User {
        id: ID!
        name: String
        birthday: Date # Formiql Custom Type
        password: Password # Formiql Custom Type
        username: String
      }
    }
  `
];

const resolvers = { /* optional, defaults are Ant Design */
      input: {
        string,
        int,
        float,
        /* Custom Formiql Types */
        dollar,
        decimal,
        phone,
        email,
        date,
        password,
      },
      textarea,
      select,
      option,
      button: {
        cancel,
        submit,
        radio
      },
      toggle,
  }
};

class Main {
  render() {
    return (
      <Formiql.Provider types={typeDefs} resolvers={resolvers} >
        <Formiql.Form
          onSubmit={data => console.log(data)}
          type="User"
        />
      </Formiql.Provider>
    )
  }
}
```
