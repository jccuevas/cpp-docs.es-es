---
title: / DEPENDENTLOADFLAG (establecer marcas de carga dependiente del valor predeterminado)
description: La opción /DEPENDENTLOADFLAG establece marcas predeterminadas para las DLL que se cargan mediante LoadLibrary
ms.custom: ''
ms.date: 05/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- dependentloadflag
dev_langs:
- C++
helpviewer_keywords:
- LINK tool [C++], dependent load flags
- -DEPENDENTLOADFLAG linker option
- linker [C++], DEPENDENTLOADFLAG
- DEPENDENTLOADFLAG linker option
- /DEPENDENTLOADFLAG linker option
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a171f3c2edbbbf614a986ff78dd2405e734a1d1
ms.sourcegitcommit: d1f576a0f59678edc3d93508cf46485138332178
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753718"
---
# <a name="dependentloadflag-set-default-dependent-load-flags"></a>/ DEPENDENTLOADFLAG (establecer marcas de carga dependiente del valor predeterminado)

Establece las marcas de carga predeterminado utiliza cuando `LoadLibrary` se usa para cargar archivos DLL.

## <a name="syntax"></a>Sintaxis

> **/ DEPENDENTLOADFLAG**[**:**_loadflags_]

### <a name="arguments"></a>Argumentos

|||
|-|-|
*loadflags*|Un valor entero de 16 bits de estilo "C" opcional en decimal, octal con un cero a la izquierda o hexadecimal con inicial `0x`, que especifica las marcas de carga dependientes que se aplicará a todos los [LoadLibrary](https://go.microsoft.com/fwlink/p/?LinkID=259187) llamadas. El valor predeterminado es 0.

## <a name="remarks"></a>Comentarios

Esta opción es nueva en Visual Studio de 2017 y solo se aplica a aplicaciones que se ejecutan en Windows 10 RS1 y versiones posteriores. Esta opción se omite para otros sistemas operativos que ejecutan la aplicación.

En sistemas operativos compatibles, esta opción tiene el efecto de cambiar las llamadas a `LoadLibrary("dependent.dll")` en el equivalente de `LoadLibraryEx("dependent.dll", 0, loadflags)`. Las llamadas a [LoadLibraryEx](https://go.microsoft.com/fwlink/p/?LinkID=236091) no se ven afectados. Esta opción no aplica de forma recursiva a archivos DLL cargados por la aplicación.

Esta marca se puede utilizar para evitar que el archivo DLL plantación ataques. Por ejemplo, si una aplicación usa `LoadLibrary` para cargar una DLL dependiente, un atacante puede implantar un archivo DLL con el mismo nombre en la ruta de acceso de búsqueda que usa `LoadLibrary`, como el directorio actual, que puede comprobarse antes de directorios del sistema si es el modo seguro de búsqueda DLL deshabilitado. Modo seguro de búsqueda DLL coloca el directorio del usuario actual más adelante en el orden de búsqueda y está habilitado de forma predeterminada en Windows XP SP2 y versiones posteriores. Para obtener más información, consulte [orden de búsqueda de biblioteca de vínculos dinámicos](https://msdn.microsoft.com/library/windows/desktop/ms682586.aspx).

Si especifica la opción de vínculo `/DEPENDENTLOADFLAG:0xA00` (el valor de los indicadores combinados `LOAD_LIBRARY_SEARCH_APPLICATION_DIR | LOAD_LIBRARY_SEARCH_SYSTEM32`), a continuación, incluso si se deshabilita el modo seguro de búsqueda DLL en el equipo del usuario, la ruta de acceso de búsqueda DLL se limita a directorios protegidos que están más difíciles que un atacante cambiar. Para obtener información sobre las marcas disponibles y sus valores simbólicos y numéricos, vea el *dwFlags* descripción del parámetro en [LoadLibraryEx](https://go.microsoft.com/fwlink/p/?LinkID=236091).

### <a name="to-set-the-dependentloadflag-linker-option-in-the-visual-studio-development-environment"></a>Para establecer la opción de vinculador DEPENDENTLOADFLAG en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. Escriba la opción en **opciones adicionales**.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

- [Establecer las opciones del vinculador](setting-linker-options.md)
- [Opciones del vinculador](linker-options.md)
- [Cómo vincular implícitamente a un archivo DLL](../linking-an-executable-to-a-dll.md#linking-implicitly)
- [Determinar qué método de vinculación para usar](../linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)
- [LoadLibrary](https://go.microsoft.com/fwlink/p/?LinkID=259187)
- [LoadLibraryEx](https://go.microsoft.com/fwlink/p/?LinkID=236091)
- [Orden de búsqueda de la biblioteca de vínculos dinámicos](https://msdn.microsoft.com/library/windows/desktop/ms682586.aspx)
