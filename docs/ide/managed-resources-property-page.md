---
title: Página de propiedades Recursos administrados | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManagedResourceCompilerTool.ResourceFileName
- VC.Project.VCManagedResourceCompilerTool.OutputFileName
- VC.Project.VCManagedResourceCompilerTool.DefaultLocalizedResources
dev_langs:
- C++
helpviewer_keywords:
- Managed Resources property page
ms.assetid: 80b80384-ee55-494d-9f0e-907bb98cfc19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 687203787bdab69751aabf0672fe1269974b3014
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399615"
---
# <a name="managed-resources-property-page"></a>página de propiedades Recursos administrados

Habilita opciones para el compilador de recursos.

La página de propiedades **Recursos administrados** contiene las propiedades siguientes:

- **Nombre lógico del recurso**

   Especifica el *nombre lógico* del archivo .resources intermedio que se genera. El nombre lógico es el que se usa para cargar el recurso. Si no se especifica ningún nombre lógico, se usa el nombre de archivo de recursos (.resx) como el nombre lógico.

- **Nombre del archivo de salida**

   Especifica el nombre del archivo de salida final al que contribuye este archivo de recursos (.resx).

- **Recursos adaptados predeterminados**

   Especifica si el archivo .resx indicado contribuye a los recursos predeterminados o a un archivo .dll satélite.

Para obtener información sobre cómo acceder a las páginas de propiedades **Recursos administrados**, vea [Trabajar con propiedades de proyecto](../ide/working-with-project-properties.md).

## <a name="see-also"></a>Vea también

[Using RC (The RC Command Line)](/windows/desktop/menurc/using-rc-the-rc-command-line-) [Uso de RC (la línea de comandos de RC)]<br>
[Páginas de propiedades](../ide/property-pages-visual-cpp.md)<br>
[/ASSEMBLYRESOURCE (Insertar un recurso administrado)](../build/reference/assemblyresource-embed-a-managed-resource.md)