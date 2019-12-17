```javascript
import PropTypes from 'prop-types';

const ComponentName = ({props}) => (
const { name } = props;
 <div>{`Hi ${name}! Well, Hello World!`}</div>
);

ComponentName.propTypes = {
  name: PropTypes.string
};

ComponentName.defaultProps = {
  name: 'Stranger'
};

export default ComponentName;
```