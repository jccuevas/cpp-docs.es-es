---
title: "C&#243;mo: Recuperar texto del Portapapeles (C++/CLI) | Microsoft Docs"
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
  - "Portapapeles, recuperar texto"
  - "texto, recuperar del Portapapeles"
ms.assetid: 99e77ba0-8573-4030-92d8-de8aa7623ee4
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Recuperar texto del Portapapeles (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el ejemplo de código siguiente se utiliza la función miembro <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> para devolver un puntero a la interfaz <xref:System.Windows.Forms.IDataObject>.  Esta interfaz se puede consultar a continuación para conocer el formato de los datos y utilizarse para recuperar los datos reales.  
  
## Ejemplo  
  
```  
// read_clipboard.cpp  
// compile with: /clr  
#using <system.dll>  
#using <system.Drawing.dll>  
#using <system.windows.forms.dll>  
  
using namespace System;  
using namespace System::Windows::Forms;  
  
[STAThread] int main( )  
{  
   IDataObject^ data = Clipboard::GetDataObject( );  
  
   if (data)  
   {  
      if (data->GetDataPresent(DataFormats::Text))   
      {  
         String^ text = static_cast<String^>  
           (data->GetData(DataFormats::Text));  
         Console::WriteLine(text);   
      }  
      else  
         Console::WriteLine("Nontext data is in the Clipboard.");  
   }  
   else   
   {  
      Console::WriteLine("No data was found in the Clipboard.");  
   }  
  
   return 0;  
}  
```  
  
## Vea también  
 [Operaciones de Windows](../dotnet/windows-operations-cpp-cli.md)   
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)