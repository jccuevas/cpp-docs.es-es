---
title: "Cómo: dibujar formas con .NET Framework | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- GDI+, drawing shapes
- drawing, shapes
- shapes
- shapes, drawing
ms.assetid: ffad5ae7-6ef4-4550-8940-be3f209a101d
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9c9c2fedb4bb07fa2301368e4bd7b62fb636d3fb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-draw-shapes-with-the-net-framework"></a>Cómo: Dibujar formas con .NET Framework
El siguiente ejemplo de código utiliza el <xref:System.Drawing.Graphics> clase para modificar el <xref:System.Windows.Forms.Form.OnPaint%2A> controlador de eventos para recuperar un puntero a la <xref:System.Drawing.Graphics> objeto para el formulario principal. This (puntero), a continuación, se usa para establecer el color de fondo del formulario y dibujar una línea y un arco utilizando la <xref:System.Drawing.Graphics.DrawLine%2A?displayProperty=fullName> y <xref:System.Drawing.Graphics.DrawArc%2A> métodos.  
  
> [!NOTE]
>  GDI + se incluye con Windows XP y está disponible como componente redistribuible para Windows NT 4.0 Service Pack 6, Windows 2000, Windows 98 y Windows Millennium Edition. Para descargar el último redistribuible, vea [http://go.microsoft.com/fwlink/?linkid=11232](http://go.microsoft.com/fwlink/?linkid=11232). 
  
## <a name="example"></a>Ejemplo  
  
```  
#using <system.drawing.dll>  
using namespace System;  
using namespace System::Drawing;  
// ...  
protected:   
virtual Void Form1::OnPaint(PaintEventArgs^ pe ) override  
{  
   Graphics^ g = pe->Graphics;  
   g->Clear(Color::AntiqueWhite);  
  
   Rectangle rect = Form::ClientRectangle;  
   Rectangle smallRect;  
   smallRect.X = rect.X + rect.Width / 4;  
   smallRect.Y = rect.Y + rect.Height / 4;  
   smallRect.Width = rect.Width / 2;  
   smallRect.Height = rect.Height / 2;  
  
   Pen^ redPen = gcnew Pen(Color::Red);  
   redPen->Width = 4;  
   g->DrawLine(redPen, 0, 0, rect.Width, rect.Height);  
  
   Pen^ bluePen = gcnew Pen(Color::Blue);  
   bluePen->Width = 10;  
   g->DrawArc( bluePen, smallRect, 90, 270 );  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Programación de .NET con C++ / CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [Espacio de nombres Drawing](https://msdn.microsoft.com/en-us/library/system.drawing.aspx)