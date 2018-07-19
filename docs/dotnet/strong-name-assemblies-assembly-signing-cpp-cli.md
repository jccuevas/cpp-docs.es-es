---
title: Ensamblados de nombre seguro (firma de ensamblados) (C++ / CLI) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- assemblies [C++]
- signing assemblies
- .NET Framework [C++], assembly signing
- assemblies [C++], signing
- linker [C++], assembly signing
- strong-named assemblies [C++]
ms.assetid: c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5d7ae911d2572a35ee8dbb21d5484b4679b64c4d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169197"
---
# <a name="strong-name-assemblies-assembly-signing-ccli"></a>Ensamblados de nombre seguro (Firma de ensamblados) (C++/CLI)
Este tema describe cómo se puede firmar el ensamblado, a menudo se denomina dando un nombre seguro a su ensamblado.  
  
## <a name="remarks"></a>Comentarios  
 Cuando utilice Visual C++, use las opciones del vinculador para firmar el ensamblado para evitar problemas relacionados con los atributos CLR para firmar el ensamblado:  
  
-   <xref:System.Reflection.AssemblyDelaySignAttribute>  
  
-   <xref:System.Reflection.AssemblyKeyFileAttribute>  
  
-   <xref:System.Reflection.AssemblyKeyNameAttribute>  
  
 Razones para no utilizar los atributos incluyen el hecho de que el nombre de clave es visible en los metadatos de ensamblado, que pueden suponer un riesgo de seguridad si el nombre de archivo incluye información confidencial. Además, el proceso de compilación utilizado por el entorno de desarrollo de Visual C++ invalidará la clave con la que se firma el ensamblado si usa atributos CLR para asignar un nombre seguro al ensamblado y, a continuación, ejecute una herramienta de procesamiento posterior como mt.exe en el ensamblado.  
  
 Compilar en la línea de comandos, utilice las opciones del vinculador para firmar el ensamblado y, a continuación, ejecutar una herramienta de procesamiento posterior (como mt.exe), debe volver a firmar el ensamblado con sn.exe. Como alternativa, puede compilar y retrasar la firma del ensamblado y después de ejecutar herramientas de procesamiento posterior, completar la firma.  
  
 Si utiliza los atributos de firma al compilar en el entorno de desarrollo, se puede firmar el ensamblado correctamente llamando explícitamente a sn.exe ([Sn.exe (herramienta de nombre seguro)](/dotnet/framework/tools/sn-exe-strong-name-tool)) en un evento posterior a la compilación. Para obtener más información, consulte [especificar eventos de compilación](../ide/specifying-build-events.md). Los tiempos de compilación pueden ser menor si usa atributos y un evento posterior a la compilación, en comparación con el uso de opciones de un vinculador.  
  
 Las siguientes opciones del vinculador admiten la firma de un ensamblado:  
  
-   [/DELAYSIGN (Firmar parcialmente un ensamblado)](../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/KEYFILE (Especificar una clave o par de claves para firmar un ensamblado)](../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/KEYCONTAINER (Especificar un contenedor de claves para firmar un ensamblado)](../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
 Para obtener más información sobre los ensamblados seguro, consulte [crear y utilizar ensamblados](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies).  
  
## <a name="see-also"></a>Vea también  
 [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)