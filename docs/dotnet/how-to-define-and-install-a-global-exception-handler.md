---
title: 'Cómo: Definir e instalar un controlador de excepciones global'
ms.date: 11/04/2016
helpviewer_keywords:
- handlers, global
ms.assetid: dd88a812-3bc7-4ce8-8283-4b674c246534
ms.openlocfilehash: 9c6f355bc43fc53d2b8d27a1ee69c059d0f50692
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534542"
---
# <a name="how-to-define-and-install-a-global-exception-handler"></a>Cómo: Definir e instalar un controlador de excepciones global

El ejemplo de código siguiente muestra las excepciones no controladas de cómo se pueden capturar. El formulario de ejemplo contiene un botón que, cuando se presionan, realiza una referencia nula, provocando que se produzca una excepción. Esta funcionalidad representa un error de código típico. El controlador de excepciones en toda la aplicación instalado por la función principal detecta la excepción resultante.

Esto se logra enlazando un delegado para el <xref:System.Windows.Forms.Application.ThreadException> eventos. En este caso, excepciones posteriores se envían a la `App::OnUnhandled` método.

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