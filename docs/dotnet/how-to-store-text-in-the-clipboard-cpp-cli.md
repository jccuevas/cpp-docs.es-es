---
title: "C&#243;mo: Almacenar texto en el Portapapeles (C++/CLI) | Microsoft Docs"
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
  - "Portapapeles, almacenar texto"
  - "texto, almacenar en el Portapapeles"
ms.assetid: 9996023f-b700-47ad-8ad9-1ba201eaa5a6
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Almacenar texto en el Portapapeles (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el ejemplo de código siguiente se utiliza el objeto <xref:System.Windows.Forms.Clipboard> definido en el espacio de nombres <xref:System.Windows.Forms> para almacenar una cadena.  Este objeto proporciona dos funciones miembro: <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> y <xref:System.Windows.Forms.Clipboard.GetDataObject%2A>.  Los datos se almacenan en el Portapapeles mediante el envío de cualquier objeto derivado de <xref:System.Object> a <xref:System.Windows.Forms.Clipboard.SetDataObject%2A>.  
  
## Ejemplo  
  
```  
// store_clipboard.cpp  
// compile with: /clr  
#using <System.dll>  
#using <System.Drawing.dll>  
#using <System.Windows.Forms.dll>  
  
using namespace System;  
using namespace System::Windows::Forms;  
  
[STAThread] int main()  
{  
   String^ str = "This text is copied into the Clipboard.";  
  
   // Use 'true' as the second argument if  
   // the data is to remain in the clipboard  
   // after the program terminates.  
   Clipboard::SetDataObject(str, true);  
  
   Console::WriteLine("Added text to the Clipboard.");  
  
   return 0;  
}  
```  
  
## Vea también  
 [Cómo: Recuperar texto del Portapapeles](../dotnet/how-to-retrieve-text-from-the-clipboard-cpp-cli.md)   
 [Operaciones de Windows](../dotnet/windows-operations-cpp-cli.md)   
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)