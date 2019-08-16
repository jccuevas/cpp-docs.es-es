---
title: /ALLOWISOLATION (Manifestar bucle)
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION
- VC.Project.VCLinkerTool.AllowIsolation
helpviewer_keywords:
- -ALLOWISOLATION linker option
- /ALLOWISOLATION linker option
ms.assetid: 6d41851e-b3c1-4bdf-beaa-031773089d6f
ms.openlocfilehash: 7c799f3d44428643bccc2869255ffa4e9d194d70
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493134"
---
# <a name="allowisolation-manifest-lookup"></a>/ALLOWISOLATION (Manifestar bucle)

Especifica el comportamiento de la búsqueda de manifiesto.

## <a name="syntax"></a>Sintaxis

```
/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>Comentarios

**/ALLOWISOLATION: no** indica que los archivos DLL se cargan como si no hubiera ningún manifiesto y hace que el `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` enlazador establezca el bit en `DllCharacteristics` el campo del encabezado opcional.

**/ALLOWISOLATION** hace que el sistema operativo realice búsquedas y cargas de manifiestos.

**/ALLOWISOLATION** es el valor predeterminado.

Cuando el aislamiento está deshabilitado para un archivo ejecutable, el cargador de Windows no intentará encontrar un manifiesto de aplicación para el proceso recién creado. El nuevo proceso no tendrá un contexto de activación predeterminado, aunque haya un manifiesto dentro del ejecutable o colocado en el mismo directorio que el ejecutable con el nombre <em>ejecutable-nombre</em> **. exe. manifest**.

Para obtener más información, vea [referencia de archivos de manifiesto](/windows/win32/SbsCs/manifest-files-reference).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades **configuración** > del**archivo de manifiesto** del**enlazador** > .

1. Modifique la propiedad **permitir aislamiento** .

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
