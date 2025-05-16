# React Modal

Modal JSX file (`modal.jsx`)

```
import React, { useRef } from "react";
import "./modal.css"; // Import the CSS file

const Modal = () => {
  const dialogRef = useRef(null);

  const handleOpenModal = () => {
    dialogRef.current.showModal();
  };

  const handleCloseModal = () => {
    dialogRef.current.close();
  };

  const handleClickOutside = (event) => {
    const rect = dialogRef.current.getBoundingClientRect();
    const isInDialog =
      event.clientX >= rect.left &&
      event.clientX <= rect.right &&
      event.clientY >= rect.top &&
      event.clientY <= rect.bottom;

    if (!isInDialog) {
      dialogRef.current.close();
    }
  };

  return (
    <div>
      <button id="open-modal" onClick={handleOpenModal}>
        Open modal
      </button>

      <dialog id="dialog" ref={dialogRef} onClick={handleClickOutside}>
        <h2>Hello, World!</h2>
        <p className="description">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Vero, animi!
        </p>
        <button
          id="close-modal"
          className="btn"
          onClick={handleCloseModal}
          autoFocus
        >
          Close
        </button>
      </dialog>
    </div>
  );
};

export default Modal;

```

Modal CSS file (`modal.css`)

```
dialog {
  margin: auto;
  padding: 2rem;
  border: none;
  border-radius: 6px;
  opacity: 0;
  transition: all 0.3s allow-discrete;
}

dialog[open] {
  opacity: 1;
}

@starting-style {
  dialog[open] {
    opacity: 0;
  }
}

dialog::backdrop {
  background-color: rgba(50, 50, 50, 0);
  transition: all 0.3s allow-discrete;
}

dialog[open]::backdrop {
  background-color: rgba(50, 50, 50, 0.8);
}

@starting-style {
  dialog[open]::backdrop {
    background-color: rgba(50, 50, 50, 0);
  }
}

```
