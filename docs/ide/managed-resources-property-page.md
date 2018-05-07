---
title: Administrar la página de propiedades recursos | Documentos de Microsoft
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
ms.openlocfilehash: 2922a0a92a121d6838478daaf2c32f1c7a630d21
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="managed-resources-property-page"></a>página de propiedades Recursos administrados
Habilita la configuración para el compilador de recursos.  
  
 El **recursos administrados** página de propiedades contiene las siguientes propiedades:  
  
 **Nombre lógico del recurso**  
 Especifica la *nombre lógico* del archivo .resources intermedio generado. El nombre lógico es el nombre usado para cargar el recurso. Si no se especifica ningún nombre lógico, el nombre de archivo de recursos (.resx) se utiliza como el nombre lógico.  
  
 **Nombre del archivo de salida**  
 Especifica el nombre del archivo de salida final que contribuye a crear el archivo de recursos (.resx).  
  
 **Recursos localizados predeterminados**  
 Especifica si el archivo .resx determinado contribuye a los recursos predeterminados o a un archivo .dll satélite.  
  
 Para obtener información sobre cómo obtener acceso a la **recursos administrados** página de propiedades, vea [trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md).  
  
## <a name="see-also"></a>Vea también  
 [Utilizar RC (la línea de comandos RC)](http://msdn.microsoft.com/library/windows/desktop/aa381055)   
 [Páginas de propiedades](../ide/property-pages-visual-cpp.md)   
 [/ASSEMBLYRESOURCE (Insertar un recurso administrado)](../build/reference/assemblyresource-embed-a-managed-resource.md)