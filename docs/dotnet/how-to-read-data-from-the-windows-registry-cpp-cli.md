---
title: "C&#243;mo: Leer datos en el Registro de Windows (C++/CLI) | Microsoft Docs"
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
  - "Registro, leer"
  - "Visual C++, leer en el Registro de Windows"
ms.assetid: aebf52c0-acc7-40e2-adbc-d34e0a1e467e
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Leer datos en el Registro de Windows (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El ejemplo de código siguiente utiliza la clave <xref:Microsoft.Win32.Registry.CurrentUser> para leer los datos del Registro de Windows.  Primero, se enumeran las subclaves utilizando el método <xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A> y, a continuación, se abre la subclave Identities utilizando el método <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A>.  Del mismo modo que las claves raíz, cada subclave se representa mediante la clase <xref:Microsoft.Win32.RegistryKey>.  Finalmente, el nuevo objeto <xref:Microsoft.Win32.RegistryKey> se utiliza para enumerar los pares clave\/valor.  
  
## Ejemplo  
  
### Código  
  
```  
// registry_read.cpp  
// compile with: /clr  
using namespace System;  
using namespace Microsoft::Win32;  
  
int main( )  
{  
   array<String^>^ key = Registry::CurrentUser->GetSubKeyNames( );  
  
   Console::WriteLine("Subkeys within CurrentUser root key:");  
   for (int i=0; i<key->Length; i++)  
   {  
      Console::WriteLine("   {0}", key[i]);  
   }  
  
   Console::WriteLine("Opening subkey 'Identities'...");  
   RegistryKey^ rk = nullptr;  
   rk = Registry::CurrentUser->OpenSubKey("Identities");  
   if (rk==nullptr)  
   {  
      Console::WriteLine("Registry key not found - aborting");  
      return -1;  
   }  
  
   Console::WriteLine("Key/value pairs within 'Identities' key:");  
   array<String^>^ name = rk->GetValueNames( );  
   for (int i=0; i<name->Length; i++)  
   {  
      String^ value = rk->GetValue(name[i])->ToString();  
      Console::WriteLine("   {0} = {1}", name[i], value);  
   }  
  
   return 0;  
}  
```  
  
## Comentarios  
 La clase <xref:Microsoft.Win32.Registry> es simplemente un contenedor para instancias estáticas de <xref:Microsoft.Win32.RegistryKey>.  Cada instancia representa un nodo de Registro raíz.  Las instancias son <xref:Microsoft.Win32.Registry.ClassesRoot>, <xref:Microsoft.Win32.Registry.CurrentConfig>, <xref:Microsoft.Win32.Registry.CurrentUser>, <xref:Microsoft.Win32.Registry.LocalMachine> y <xref:Microsoft.Win32.Registry.Users>.  
  
 Además de ser estáticos, los objetos incluidos en la clase <xref:Microsoft.Win32.Registry> son de sólo lectura.  Por otra parte, las instancias de la clase <xref:Microsoft.Win32.RegistryKey> que se crean para tener acceso al contenido de los objetos del Registro también son de sólo lectura.  Para obtener un ejemplo de cómo hacer caso omiso de este comportamiento, vea [Cómo: Escribir datos en el Registro de Windows](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md).  
  
 Hay dos objetos adicionales en la clase <xref:Microsoft.Win32.Registry>: <xref:Microsoft.Win32.Registry.DynData> y <xref:Microsoft.Win32.Registry.PerformanceData>.  Los dos son instancias de la clase <xref:Microsoft.Win32.RegistryKey>.  El objeto <xref:Microsoft.Win32.Registry.DynData> contiene información dinámica del Registro, que solo se admite en Windows 98 y Windows Me.  El objeto <xref:Microsoft.Win32.Registry.PerformanceData> se puede usar para tener acceso a información del contador de rendimiento para aplicaciones que usan el sistema de supervisión de rendimiento de Windows.  El nodo <xref:Microsoft.Win32.Registry.PerformanceData> representa información que no está almacenada realmente en el Registro y, por consiguiente, no se puede ver utilizando Regedit.exe.  
  
## Vea también  
 [Cómo: Escribir datos en el Registro de Windows](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md)   
 [Operaciones de Windows](../dotnet/windows-operations-cpp-cli.md)   
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)