---
title: "Administrar la página de propiedades recursos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCManagedResourceCompilerTool.ResourceFileName
- VC.Project.VCManagedResourceCompilerTool.OutputFileName
- VC.Project.VCManagedResourceCompilerTool.DefaultLocalizedResources
dev_langs: C++
helpviewer_keywords: Managed Resources property page
ms.assetid: 80b80384-ee55-494d-9f0e-907bb98cfc19
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b8683c9212a25a5b278405c2d2c31d7fc607d0f5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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