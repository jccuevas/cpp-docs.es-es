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
ms.openlocfilehash: a2fe0896a8fbd8b8c0a8f68847ee138017eaa36b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43215506"
---
# <a name="managed-resources-property-page"></a>página de propiedades Recursos administrados
Habilita opciones para el compilador de recursos.  
  
 La página de propiedades **Recursos administrados** contiene las propiedades siguientes:  
  
 **Nombre lógico del recurso**  
 Especifica el *nombre lógico* del archivo .resources intermedio que se genera. El nombre lógico es el que se usa para cargar el recurso. Si no se especifica ningún nombre lógico, se usa el nombre de archivo de recursos (.resx) como el nombre lógico.  
  
 **Nombre del archivo de salida**  
 Especifica el nombre del archivo de salida final al que contribuye este archivo de recursos (.resx).  
  
 **Recursos adaptados predeterminados**  
 Especifica si el archivo .resx indicado contribuye a los recursos predeterminados o a un archivo .dll satélite.  
  
 Para obtener información sobre cómo acceder a las páginas de propiedades **Recursos administrados**, vea [Trabajar con propiedades de proyecto](../ide/working-with-project-properties.md).  
  
## <a name="see-also"></a>Vea también  
 [Using RC (The RC Command Line)](https://msdn.microsoft.com/library/windows/desktop/aa381055)  (Uso de RC (la línea de comandos de RC))  
 [Páginas de propiedades](../ide/property-pages-visual-cpp.md)   
 [/ASSEMBLYRESOURCE (Insertar un recurso administrado)](../build/reference/assemblyresource-embed-a-managed-resource.md)