---
title: "-ALLOWISOLATION (búsqueda de manifiesto) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /ALLOWISOLATION
- VC.Project.VCLinkerTool.AllowIsolation
dev_langs:
- C++
helpviewer_keywords:
- -ALLOWISOLATION linker option
- /ALLOWISOLATION linker option
ms.assetid: 6d41851e-b3c1-4bdf-beaa-031773089d6f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d0ca939021a6fc530b11c6ec66fc74cc012da1c9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="allowisolation-manifest-lookup"></a>/ALLOWISOLATION (Manifestar bucle)
Especifica el comportamiento de la búsqueda de manifiesto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/ALLOWISOLATION[:NO]  
```  
  
## <a name="remarks"></a>Comentarios  
 **/ALLOWISOLATION:no** indica la DLL se cargan como si no hubiera ningún manifiesto y hace que el vinculador establecer el `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` de bits en el encabezado opcional `DllCharacteristics` campo.  
  
 **/ ALLOWISOLATION** hace que el sistema operativo realice búsquedas y cargas de manifiestos.  
  
 **/ ALLOWISOLATION** es el valor predeterminado.  
  
 Cuando se deshabilita el aislamiento de un archivo ejecutable, el cargador de Windows no intentará encontrar un manifiesto de aplicación para el proceso recién creado. El nuevo proceso no tendrá un contexto de activación predeterminado, incluso si hay un manifiesto dentro del ejecutable o en el mismo directorio que el ejecutable con el nombre *nombre de archivo ejecutable***. exe.manifest**.  
  
 Para obtener más información, consulte [Manifest Files Reference](http://msdn.microsoft.com/library/aa375632).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Expanda el **propiedades de configuración** nodo.  
  
3.  Expanda el **vinculador** nodo.  
  
4.  Seleccione el **archivo de manifiesto** página de propiedades.  
  
5.  Modificar el **Permitir aislamiento** propiedad.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)