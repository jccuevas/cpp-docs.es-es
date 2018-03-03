---
title: "-DYNAMICBASE (uso dirección espacio selección aleatoria del diseño) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.RandomizedBaseAddress
dev_langs:
- C++
helpviewer_keywords:
- -DYNAMICBASE linker option
- /DYNAMICBASE linker option
- DYNAMICBASE linker option
ms.assetid: 6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1458070f85678d30c716622bf57740d90feb65d8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="dynamicbase-use-address-space-layout-randomization"></a>/DYNAMICBASE (Usar selección aleatoria del diseño del espacio de direcciones)
Especifica si se generará una imagen ejecutable que se pueda reorganizar aleatoriamente en tiempo de carga mediante el uso de la característica de selección aleatoria (ASLR) de diseño del espacio de direcciones de [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/DYNAMICBASE[:NO]  
```  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, / DYNAMICBASE está activada.  
  
 Esta opción modifica el encabezado de un archivo ejecutable para indicar si la aplicación se debe reorganizar aleatoriamente en tiempo de carga.  
  
 Selección aleatoria del diseño de espacio de direcciones se admite en [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)].  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Para establecer esta opción del vinculador en Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Expanda el **propiedades de configuración** nodo.  
  
3.  Expanda el **vinculador** nodo.  
  
4.  Seleccione el **avanzadas** página de propiedades.  
  
5.  Modificar el **dirección Base aleatoria** propiedad.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RandomizedBaseAddress%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)