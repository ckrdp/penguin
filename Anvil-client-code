from ._anvil_designer import Form1Template
from anvil import *
import anvil.server

class Form1(Form1Template):
  def __init__(self, **properties):
    # Set Form properties and Data Bindings.
    self.init_components(**properties)

    # Any code you write here will run before the form opens.

  def primary_color_1_click(self, **event_args):
    """This method is called when the button is clicked"""
    if self.txt_cl.text is None or self.txt_fl.text is None or self.txt_bm.text is None or self.txt_cd.text is None or self.ddl1.selected_value is None or (self.rdmale.selected==False and self.rdfem.selected==False):
      flag=0
    else:
      flag=1

    if flag:
      # code for radio button
      if self.rdmale.selected:
        sex=self.rdmale.value
      if self.rdfem.selected:
        sex=self.rdfem.value
      #Code for Island
      if self.ddl1.selected_value== "Biscoe" :
        Island=0
      elif self.ddl1.selected_value == "Dream":
        Island=1
      elif self.ddl1.selected_value=="Torgersen":
        Island=2
      
      res = anvil.server.call('predict_pen', 
                                self.txt_cl.text,
                                self.txt_fl.text,
                                self.txt_bm.text,
                                self.txt_cd.text,
                                float(Island),
                                float(sex))
    # If a category is returned set our species 
      if res:
        self.lbl_res.visible = True
        self.lbl_res.text = "The species is " + res.capitalize()
    else:
      self.lbl_res.visible = True
      self.lbl_res.text="Fill Necessary Details !!"

