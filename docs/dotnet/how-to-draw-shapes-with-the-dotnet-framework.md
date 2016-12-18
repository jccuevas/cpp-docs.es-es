---
title: "C&#243;mo: Dibujar formas con .NET Framework | Microsoft Docs"
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
  - "dibujar, formas"
  - "GDI+, dibujar formas"
  - "formas"
  - "formas, dibujar"
ms.assetid: ffad5ae7-6ef4-4550-8940-be3f209a101d
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Dibujar formas con .NET Framework
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El ejemplo de código siguiente utiliza la clase <xref:System.Drawing.Graphics> para modificar el controlador de eventos <xref:System.Windows.Forms.Form.OnPaint%2A> para recuperar un puntero al objeto <xref:System.Drawing.Graphics> para el formulario principal.  Este puntero se utiliza posteriormente para establecer el color de fondo del formulario y dibujar una línea y un arco utilizando los métodos <xref:System.Drawing.Graphics.DrawLine%2A?displayProperty=fullName> y <xref:System.Drawing.Graphics.DrawArc%2A>.  
  
> [!NOTE]
>  GDI\+ se incluye con Windows XP y está disponible como componente redistribuible con Windows NT 4.0 SP 6, Windows 2000, Windows 98 y Windows Me.  Para descargar el último redistribuible, vea [http:\/\/go.microsoft.com\/fwlink\/?linkid\=11232](http://go.microsoft.com/fwlink/?linkid=11232).  Para obtener más información, vea [GDI\+](_gdiplus_GDI_start_cpp).  
  
## Ejemplo  
  
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
  
## Vea también  
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)   
 [System::Drawing \(Espacio de nombres\)](https://msdn.microsoft.com/en-us/library/system.drawing.aspx)