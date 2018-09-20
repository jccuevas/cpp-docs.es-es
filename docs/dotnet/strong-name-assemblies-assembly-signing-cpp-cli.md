---
title: Ensamblados de nombre seguro (firma de ensamblados) (C++ / c++ / CLI) | Microsoft Docs
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
ms.openlocfilehash: 75b7df96b9366680b69d40dea866fb3067a507b7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430911"
---
# <a name="strong-name-assemblies-assembly-signing-ccli"></a>Ensamblados de nombre seguro (Firma de ensamblados) (C++/CLI)

En este tema se describe cómo se puede firmar el ensamblado, a menudo se denomina dar un nombre seguro a su ensamblado.

## <a name="remarks"></a>Comentarios

Cuando se usa Visual C++, use las opciones del vinculador para firmar el ensamblado para evitar problemas relacionados con los atributos CLR para firmar el ensamblado:

- <xref:System.Reflection.AssemblyDelaySignAttribute>

- <xref:System.Reflection.AssemblyKeyFileAttribute>

- <xref:System.Reflection.AssemblyKeyNameAttribute>

Razones para no utilizar los atributos incluyen el hecho de que el nombre de clave es visible en los metadatos de ensamblado, que pueden suponer un riesgo de seguridad si el nombre de archivo incluye información confidencial. Además, el proceso de compilación usado por el entorno de desarrollo de Visual C++ invalidará la clave con el que el ensamblado está firmado si usa atributos de CLR para asignar un nombre seguro al ensamblado y, a continuación, ejecute una herramienta como mt.exe posteriores al procesamiento en el ensamblado.

Si la compilación en la línea de comandos, utilice las opciones del vinculador para firmar el ensamblado y, a continuación, ejecutar una herramienta de procesamiento posterior (como mt.exe), deberá volver a firmar el ensamblado con sn.exe. Como alternativa, puede crear y retrasar la firma del ensamblado y después de ejecutar herramientas de procesamiento posterior, completar la firma.

Si usa los atributos de firma al compilar en el entorno de desarrollo, se puede firmar el ensamblado correctamente llamando explícitamente a sn.exe ([Sn.exe (Strong Name Tool)](/dotnet/framework/tools/sn-exe-strong-name-tool)) en un evento posterior a la compilación. Para obtener más información, vea [Especificar eventos de compilación](../ide/specifying-build-events.md). Los tiempos de compilación pueden ser menor si usa atributos y un evento posterior a la compilación, en comparación con usar las opciones de un vinculador.

Las siguientes opciones del vinculador admiten la firma de ensamblados:

- [/DELAYSIGN (Firmar parcialmente un ensamblado)](../build/reference/delaysign-partially-sign-an-assembly.md)

- [/KEYFILE (Especificar una clave o par de claves para firmar un ensamblado)](../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/KEYCONTAINER (Especificar un contenedor de claves para firmar un ensamblado)](../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)

Para obtener más información sobre los ensamblados seguro, consulte [crear y utilizar ensamblados](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies).

## <a name="see-also"></a>Vea también

[Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)