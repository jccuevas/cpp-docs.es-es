---
title: "C&#243;mo: Implementar una arquitectura de componentes complementarios mediante reflexi&#243;n (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "complementos [C++]"
  - "reflexión [C++}, complementos"
ms.assetid: 4f31e42b-78d1-48b9-8fdc-f28c75e8e77e
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Implementar una arquitectura de componentes complementarios mediante reflexi&#243;n (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los ejemplos de código siguientes muestran el uso de reflexión para implementar una arquitectura de "complemento" simple.  La primera lista es la aplicación y la segunda es el complemento.  La aplicación es un formulario de documento múltiple que se rellena mediante cualquier clase basada en formulario que se encuentre en el archivo DLL de complemento suministrado como argumento de línea de comandos.  
  
 La aplicación intenta cargar el ensamblado proporcionado mediante el método <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>.  Si lo logra, los tipos incluidos en el ensamblado se enumeran utilizando el método <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName>.  A continuación, se comprueba la compatibilidad de cada tipo mediante el método <xref:System.Type.IsAssignableFrom%2A?displayProperty=fullName>.  En este ejemplo, las clases incluidas en el ensamblado proporcionado se deben derivar de la clase <xref:System.Windows.Forms.Form> para poderse considerar complementos.  
  
 Después, se crean instancias de las clases compatibles con el método <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>, que acepta <xref:System.Type> como argumento y devuelve un puntero a una nueva instancia.  Cada nueva instancia se asocia a continuación al formulario y se muestra.  
  
 Observe que el método <xref:System.Reflection.Assembly.Load%2A> no acepta nombres de ensamblado que incluyan la extensión de archivo.  La función principal en la aplicación recorta cualquier extensión proporcionada, por lo que el ejemplo de código siguiente funciona en cualquier caso.  
  
## Ejemplo  
 El código siguiente define la aplicación que acepta complementos.  Como primer argumento, se debe proporcionar un nombre de ensamblado.  Este ensamblado debería contener por lo menos un tipo derivado <xref:System.Windows.Forms.Form> público.  
  
```  
// plugin_application.cpp  
// compile with: /clr /c  
#using <system.dll>  
#using <system.drawing.dll>  
#using <system.windows.forms.dll>  
  
using namespace System;  
using namespace System::Windows::Forms;  
using namespace System::Reflection;  
  
ref class PluggableForm : public Form  {  
public:  
   PluggableForm() {}  
   PluggableForm(Assembly^ plugAssembly) {  
      Text = "plug-in example";  
      Size = Drawing::Size(400, 400);  
      IsMdiContainer = true;  
  
      array<Type^>^ types = plugAssembly->GetTypes( );  
      Type^ formType = Form::typeid;  
  
      for (int i = 0 ; i < types->Length ; i++) {  
         if (formType->IsAssignableFrom(types[i])) {  
            // Create an instance given the type description.  
            Form^ f = dynamic_cast<Form^> (Activator::CreateInstance(types[i]));  
            if (f) {  
               f->Text = types[i]->ToString();  
               f->MdiParent = this;  
               f->Show();  
            }  
         }  
      }  
   }  
};  
  
int main() {  
   Assembly^ a = Assembly::LoadFrom("plugin_application.exe");  
   Application::Run(gcnew PluggableForm(a));  
}  
```  
  
## Ejemplo  
 El código siguiente define tres clases derivadas de <xref:System.Windows.Forms.Form>.  Cuando el nombre del ensamblado resultante se pasa al ejecutable de la lista anterior, se detecta cada una de estas tres clases y se crean instancias para ellas, a pesar del hecho de que fuesen todas desconocidas para la aplicación de hospedaje en tiempo de compilación.  
  
```  
// plugin_assembly.cpp  
// compile with: /clr /LD  
#using <system.dll>  
#using <system.drawing.dll>  
#using <system.windows.forms.dll>  
  
using namespace System;  
using namespace System::Windows::Forms;  
using namespace System::Reflection;  
using namespace System::Drawing;  
  
public ref class BlueForm : public Form {  
public:  
   BlueForm() {  
      BackColor = Color::Blue;  
   }  
};  
  
public ref class CircleForm : public Form {  
protected:  
   virtual void OnPaint(PaintEventArgs^ args) override {  
      args->Graphics->FillEllipse(Brushes::Green, ClientRectangle);  
   }  
};  
  
public ref class StarburstForm : public Form {  
public:  
   StarburstForm(){  
      BackColor = Color::Black;  
   }  
protected:  
   virtual void OnPaint(PaintEventArgs^ args) override {  
      Pen^ p = gcnew Pen(Color::Red, 2);  
      Random^ r = gcnew Random( );  
      Int32 w = ClientSize.Width;  
      Int32 h = ClientSize.Height;  
      for (int i=0; i<100; i++) {  
         float x1 = w / 2;  
         float y1 = h / 2;  
         float x2 = r->Next(w);  
         float y2 = r->Next(h);  
         args->Graphics->DrawLine(p, x1, y1, x2, y2);  
      }  
   }  
};  
```  
  
## Vea también  
 [Reflexión](../dotnet/reflection-cpp-cli.md)