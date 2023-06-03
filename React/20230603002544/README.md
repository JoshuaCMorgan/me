# Create responsive CSS in React with `useRef`

The navigation bar is such that we have logo, hamburger menu and navigation links.

The navigation links are contained inside a `div` element. They can be hidden or shown, depending on the user clicking the hamburger menue. The links are also either show in a row when display is large or in a column and hidden when the display is small.
The link's hidden and show state occurs through the CSS property `overflow` and `height`. Overflow is always hidden and the height of the div changes depending in the user's interaction with the hamburger.

In the code below, the `button` is what toggles the navigation links. When the user clicks it, the height of the link-container `div` changes.

To make the change happen, we use React references. Every time state changes, when `showLink` changes, we also changes the height of the links container. It's done with the object `linkStyles` that we create and pass in as a prop. The main worker allowing us to do this is `getBoundingClientRect`, which gives us the dimensions.

```js
import { useState, useRef } from "react";
import { FaBars } from "react-icons/fa";
import { links, social } from "../data";
import logo from "../assets/images/myLogo.svg";

const Navbar = () => {
  const [showLinks, setShowLinks] = useState(false);
  const linksContainerRef = useRef(null);
  const linksRef = useRef(null);

  const toggleLinks = () => {
    setShowLinks(!showLinks);
  };

  const linkStyles = {
    height: showLinks
      ? `${linksRef.current.getBoundingClientRect().height}px`
      : "0px",
  };

  return (
    <nav>
      <div className="nav-center">
        <div className="nav-header">
          <img src={logo} className="logo" alt="logo" />
          <button className="nav-toggle" onClick={toggleLinks}>
            <FaBars />
          </button>
        </div>
        <div
          className="links-container"
          ref={linksContainerRef}
          style={linkStyles}
        >
          <ul className="links" ref={linksRef}>
            {links.map((link) => {
              const { id, url, text } = link;
              return (
                <li key={id}>
                  <a href={url}>{text}</a>
                </li>
              );
            })}
          </ul>
        </div>
      </div>
    </nav>
  );
};

export default Navbar;
```

#navbar #React #toggleLinks #showLinks #hideLinks #useRef
