---
title: "Cómo: definir e instalar un controlador de excepciones Global | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- handlers, global
ms.assetid: dd88a812-3bc7-4ce8-8283-4b674c246534
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f1d9b1125fc54ecbd75fc49b36498a99f5e86f28
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-define-and-install-a-global-exception-handler"></a>Cómo: Definir e instalar un controlador de excepciones global
En el ejemplo de código siguiente se muestra cómo las excepciones no controladas de cómo se pueden capturar. El formulario de ejemplo contiene un botón que, cuando se presionan, realiza una referencia nula, provocando que se produzca una excepción. Esta funcionalidad representa un error de código típico. Se detectó la excepción resultante mediante el controlador de excepciones de toda la aplicación instalado por la función principal.  
  
 Esto se logra mediante el enlace de un delegado para que la <xref:System.Windows.Forms.Application.ThreadException> eventos. En este caso, excepciones posteriores se envían a la `App::OnUnhandled` método.  
  
## <a name="example"></a>Ejemplo  
  
```  
// global_exception_handler.cpp  
// compile with: /clr  
#using <system.dll>  
#using <system.drawing.dll>  
#using <system.windows.forms.dll>  
  
using namespace System;  
using namespace System::Threading;  
using namespace System::Drawing;  
using namespace System::Windows::Forms;  
  
ref class MyForm : public Form  
{  
   Button^ b;  
public:  
   MyForm( )  
   {  
      b = gcnew Button( );  
      b->Text = "Do Null Access";  
      b->Size = Drawing::Size(150, 30);  
      b->Click += gcnew EventHandler(this, &MyForm::OnClick);  
      Controls->Add(b);  
   }  
   void OnClick(Object^ sender, EventArgs^ args)   
   {  
      // do something illegal, like call through a null pointer...  
      Object^ o = nullptr;  
      o->ToString( );        
   }  
};  
  
ref class App  
{  
public:  
   static void OnUnhandled(Object^ sender, ThreadExceptionEventArgs^ e)  
   {  
      MessageBox::Show(e->Exception->Message, "Global Exeception");  
      Application::ExitThread( );  
   }  
};  
  
int main()  
{  
   Application::ThreadException += gcnew   
      ThreadExceptionEventHandler(App::OnUnhandled);  
  
   MyForm^ form = gcnew MyForm( );  
   Application::Run(form);  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones](../windows/exception-handling-cpp-component-extensions.md)