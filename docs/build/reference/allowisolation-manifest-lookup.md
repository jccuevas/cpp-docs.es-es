---
title: -ALLOWISOLATION (búsqueda de manifiesto) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ALLOWISOLATION
- VC.Project.VCLinkerTool.AllowIsolation
dev_langs:
- C++
helpviewer_keywords:
- -ALLOWISOLATION linker option
- /ALLOWISOLATION linker option
ms.assetid: 6d41851e-b3c1-4bdf-beaa-031773089d6f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62f467ff467d785d17601737436e0eb1ff972f37
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205498"
---
# <a name="allowisolation-manifest-lookup"></a>/ALLOWISOLATION (Manifestar bucle)
Especifica el comportamiento de la búsqueda de manifiesto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/ALLOWISOLATION[:NO]  
```  
  
## <a name="remarks"></a>Comentarios  
 **/ALLOWISOLATION:no** indica los archivos DLL se carga como si no hubiera ningún manifiesto y hace que el vinculador establezca el `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` bit en el encabezado opcional `DllCharacteristics` campo.  
  
 **/ ALLOWISOLATION** hace que el sistema operativo realice cargas y búsquedas de manifiestos.  
  
 **/ ALLOWISOLATION** es el valor predeterminado.  
  
 Cuando se deshabilita el aislamiento de un archivo ejecutable, el cargador de Windows no intentará encontrar un manifiesto de aplicación para el proceso recién creado. El nuevo proceso no tendrá un contexto de activación predeterminado, incluso si hay un manifiesto dentro del ejecutable o en el mismo directorio que el ejecutable con el nombre <em>nombre-ejecutable</em>**. exe.manifest**.  
  
 Para obtener más información, consulte [Manifest Files Reference](/windows/desktop/SbsCs/manifest-files-reference).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).  
  
2.  Expanda el nodo **Propiedades de configuración**.  
  
3.  Expanda el **vinculador** nodo.  
  
4.  Seleccione el **archivo de manifiesto** página de propiedades.  
  
5.  Modificar el **Permitir aislamiento** propiedad.  
  
## <a name="see-also"></a>Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)