---
title: Implementar una arquitectura de complemento (C++ / CLI) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- plug-ins [C++]
- reflection [C++}, plug-ins
ms.assetid: 4f31e42b-78d1-48b9-8fdc-f28c75e8e77e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4e001ef88af0727a994c309d45167787d3e6677b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33135218"
---
# <a name="how-to-implement-a-plug-in-component-architecture-using-reflection-ccli"></a>Cómo: Implementar una arquitectura de componentes complementarios mediante reflexión (C++/CLI)
Ejemplos de código siguientes muestran el uso de reflexión para implementar una arquitectura de "complemento" simple. La primera lista es la aplicación y el segundo es el complemento. La aplicación es un formulario de múltiples documentos que se rellena con las clases de basada en formularios que se encuentran en la DLL del complemento proporcionada como un argumento de línea de comandos.  
  
 La aplicación intenta cargar el ensamblado proporcionado mediante el <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> método. Si tiene éxito, los tipos dentro del ensamblado se enumeran utilizando el <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName> método. A continuación, se comprueba cada tipo de compatibilidad a través del <xref:System.Type.IsAssignableFrom%2A?displayProperty=fullName> método. En este ejemplo, las clases que se encuentran en el ensamblado proporcionado se deben derivar de la <xref:System.Windows.Forms.Form> clase para calificar como un complemento.  
  
 A continuación, se crean instancias de las clases compatibles con el <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> método, que acepta un <xref:System.Type> como argumento y devuelve un puntero a una nueva instancia. Cada nueva instancia, a continuación, se adjunta al formulario y se muestra.  
  
 Tenga en cuenta que el <xref:System.Reflection.Assembly.Load%2A> método no acepta nombres de ensamblado que incluyen la extensión de archivo. La función principal en la aplicación recorta cualquier extensión proporcionada, por lo que el ejemplo de código siguiente funciona en ambos casos.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente define la aplicación que acepta complementos. Un nombre de ensamblado se debe proporcionar como el primer argumento. Este ensamblado debe contener al menos un público <xref:System.Windows.Forms.Form> tipo derivado.  
  
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
  
## <a name="example"></a>Ejemplo  
 El código siguiente define tres clases derivadas de <xref:System.Windows.Forms.Form>. Cuando el nombre del ensamblado resultante se pasa al archivo ejecutable en la lista anterior, cada una de estas tres clases se detectará y se crea una instancia, a pesar de que fuesen todas desconocidas para la aplicación de hospedaje en tiempo de compilación.  
  
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
  
## <a name="see-also"></a>Vea también  
 [Reflexión (C++-CLI)](../dotnet/reflection-cpp-cli.md)