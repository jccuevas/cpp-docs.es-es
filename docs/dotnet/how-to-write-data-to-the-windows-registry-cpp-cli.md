---
title: "C&#243;mo: Escribir datos en el Registro de Windows (C++/CLI) | Microsoft Docs"
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
  - "Registro, escribir"
  - "Visual C++, escribir en el Registro de Windows"
ms.assetid: 3d40b978-4baa-4779-bfe3-47e2917b757f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Escribir datos en el Registro de Windows (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El ejemplo de código siguiente utiliza la clave <xref:Microsoft.Win32.Registry.CurrentUser> para crear una instancia editable de la clase <xref:Microsoft.Win32.RegistryKey> que corresponde a la clave **Software**.  El método <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A> se utiliza después para crear una nueva clave y agregarla a pares clave\/valor.  
  
## Ejemplo  
  
### Código  
  
```  
// registry_write.cpp  
// compile with: /clr  
using namespace System;  
using namespace Microsoft::Win32;  
  
int main()  
{  
   // The second OpenSubKey argument indicates that  
   // the subkey should be writable.   
   RegistryKey^ rk;  
   rk  = Registry::CurrentUser->OpenSubKey("Software", true);  
   if (!rk)  
   {  
      Console::WriteLine("Failed to open CurrentUser/Software key");  
      return -1;  
   }  
  
   RegistryKey^ nk = rk->CreateSubKey("NewRegKey");  
   if (!nk)  
   {  
      Console::WriteLine("Failed to create 'NewRegKey'");  
      return -1;  
   }  
  
   String^ newValue = "NewValue";  
   try  
   {  
      nk->SetValue("NewKey", newValue);  
      nk->SetValue("NewKey2", 44);  
   }  
   catch (Exception^)  
   {  
      Console::WriteLine("Failed to set new values in 'NewRegKey'");  
      return -1;  
   }  
  
   Console::WriteLine("New key created.");  
   Console::Write("Use REGEDIT.EXE to verify ");  
   Console::WriteLine("'CURRENTUSER/Software/NewRegKey'\n");  
   return 0;  
}  
```  
  
## Comentarios  
 Puede utilizar .NET Framework para tener acceso al Registro con las clases <xref:Microsoft.Win32.Registry> y [RegistryKey](https://msdn.microsoft.com/en-us/library/microsoft.win32.registrykey.aspx), que se definen ambas en el espacio de nombres de <xref:Microsoft.Win32>.  La clase **Registry** es un contenedor para las instancias estáticas de la clase <xref:Microsoft.Win32.RegistryKey>.  Cada instancia representa un nodo de Registro raíz.  Las instancias son <xref:Microsoft.Win32.Registry.ClassesRoot>, <xref:Microsoft.Win32.Registry.CurrentConfig>, <xref:Microsoft.Win32.Registry.CurrentUser>, <xref:Microsoft.Win32.Registry.LocalMachine> y <xref:Microsoft.Win32.Registry.Users>.  
  
## Vea también  
 [Cómo: Leer datos en el Registro de Windows](../dotnet/how-to-read-data-from-the-windows-registry-cpp-cli.md)   
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)