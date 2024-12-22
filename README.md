# SOLID-Principles_3-_Liskov-Substitution-Principle-LSP-

class Rectangle:
  def __init__(self, width, height):self.width = width
    self.height = height
  def calculate_area(self):
    return self.width * self.height
#In Rectangle, you’ve provided the .calculate_area() method, which operates withthe .width and .height instance attributes.
#Because a square is a special case of a rectangle with equal sides, you think ofderiving a Square class from Rectangle in order to reuse the code. Then, you overridethe setter method for the .width and .height attributes so that when one sidechanges, the other side also changes:
class Square(Rectangle):
  def __init__(self, side):
    super().__init__(side, side)
  def __setattr__(self, key, value):
    super().__setattr__(key, value)
    if key in ("width", "height"):
      self.__dict__["width"] = value
      self.__dict__["height"] = value
