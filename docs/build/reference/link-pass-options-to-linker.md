---
title: -link (fase de opciones al vinculador) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /link
dev_langs:
- C++
helpviewer_keywords:
- /link compiler option [C++]
- pass options to linker
- link compiler option [C++]
- linker [C++], passing options to
- -link compiler option [C++]
- cl.exe compiler [C++], passing options to linker
ms.assetid: 16902a94-c094-4328-841f-3ac94ca04848
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b22e21022162a0f9f75e41e3e0bfdce348947e1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373298"
---
# <a name="link-pass-options-to-linker"></a>/link (Pasar opciones al vinculador)
Pasa una o varias opciones del vinculador al vinculador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/link linkeroptions  
```  
  
## <a name="arguments"></a>Argumentos  
 `linkeroptions`  
 La opción del vinculador o las opciones que se pasarán al vinculador.  
  
## <a name="remarks"></a>Comentarios  
 El **/link** opción y sus opciones del vinculador deben aparecer detrás de los nombres de archivo y las opciones de CL. Se requiere un espacio entre **/link** y `linkeroptions`. Para obtener más información, consulte [establecer las opciones del vinculador](../../build/reference/setting-linker-options.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en el **vinculador** carpeta.  
  
3.  Haga clic en una página de propiedades del vinculador.  
  
4.  Modifique una o varias propiedades.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Esta opción del compilador no se puede cambiar mediante programación.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)