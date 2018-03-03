---
title: "Cómo: leer datos del registro de Windows (C++ / CLI) | Documentos de Microsoft"
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
- Visual C++, reading from Windows Registry
- registry, reading
ms.assetid: aebf52c0-acc7-40e2-adbc-d34e0a1e467e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: dfb654ba2cce069086713322624e947e14bc26f4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-read-data-from-the-windows-registry-ccli"></a>Cómo: Leer datos en el Registro de Windows (C++/CLI)
El ejemplo de código siguiente utiliza la clave <xref:Microsoft.Win32.Registry.CurrentUser> para leer los datos del Registro de Windows. En primer lugar, se enumeran las subclaves utilizando el <xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A> método y, a continuación, en la subclave Identities se abre mediante el <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> método. Del mismo modo que las claves raíz, cada subclave se representa mediante la clase <xref:Microsoft.Win32.RegistryKey>. Finalmente, el nuevo objeto <xref:Microsoft.Win32.RegistryKey> se utiliza para enumerar los pares clave/valor.  
  
## <a name="example"></a>Ejemplo  
  
### <a name="code"></a>Código  
  
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
  
## <a name="remarks"></a>Comentarios  
 La clase <xref:Microsoft.Win32.Registry> es simplemente un contenedor para instancias estáticas de <xref:Microsoft.Win32.RegistryKey>. Cada instancia representa un nodo de Registro raíz. Las instancias son <xref:Microsoft.Win32.Registry.ClassesRoot>, <xref:Microsoft.Win32.Registry.CurrentConfig>, <xref:Microsoft.Win32.Registry.CurrentUser>, <xref:Microsoft.Win32.Registry.LocalMachine> y <xref:Microsoft.Win32.Registry.Users>.  
  
 Además de ser estáticos, los objetos incluidos en la clase <xref:Microsoft.Win32.Registry> son de sólo lectura. Por otra parte, las instancias de la clase <xref:Microsoft.Win32.RegistryKey> que se crean para tener acceso al contenido de los objetos del Registro también son de sólo lectura. Para obtener un ejemplo de cómo invalidar este comportamiento, consulte [Cómo: escribir datos en el registro de Windows (C++ / CLI)](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md).  
  
 Hay dos objetos adicionales en la clase <xref:Microsoft.Win32.Registry>: <xref:Microsoft.Win32.Registry.DynData> y <xref:Microsoft.Win32.Registry.PerformanceData>. Los dos son instancias de la clase <xref:Microsoft.Win32.RegistryKey>. La <xref:Microsoft.Win32.Registry.DynData> objeto contiene información dinámica del registro, que solo se admite en Windows 98 y Windows Millennium Edition. El objeto <xref:Microsoft.Win32.Registry.PerformanceData> se puede usar para tener acceso a información del contador de rendimiento para aplicaciones que usan el sistema de supervisión de rendimiento de Windows. El <xref:Microsoft.Win32.Registry.PerformanceData> nodo representa información que no está almacenada realmente en el registro y, por tanto, no se puede ver utilizando Regedit.exe.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: escribir datos en el registro de Windows (C++ / CLI)](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md)   
 [Operaciones de Windows (C++ / CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)