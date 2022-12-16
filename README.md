# reviews_1
import {Component} from 'react'

class ReviewsCarousel extends Component {
  state = {
    count: 1,
  }

  onInc = () => {
    const {count} = this.state
    const {reviewsList} = this.props
    if (count < reviewsList.length) {
      this.setState(prevState => ({count: prevState.count + 1}))
    }
  }

  onDec = () => {
    const {count} = this.state

    if (count > 1) {
      this.setState(prevState => ({count: prevState.count - 1}))
    }
  }

  onCheck = () => {
    const {reviewsList} = this.props
    const {count} = this.state
    const item = reviewsList.find(each => each.id === count)
    return item
  }

  render() {
    const item = this.onCheck()
    return (
      <div>
        <button type="button" onClick={this.onDec} id="leftArrow">
          <img
            src="https://assets.ccbp.in/frontend/react-js/left-arrow-img.png "
            alt="left arrow"
          />
        </button>
        <h1>Reviews</h1>
        <div>
          <img src={item.imgUrl} className="emoji" alt={item.username} />
          <p>{item.username}</p>
          <p>{item.companyName}</p>
          <p>{item.description}</p>
        </div>
        <button type="button" onClick={this.onInc} id="rightArrow">
          <img
            src="https://assets.ccbp.in/frontend/react-js/right-arrow-img.png "
            alt="right arrow"
          />
        </button>
      </div>
    )
  }
}

export default ReviewsCarousel
