---
title: /NATVIS (Agregar Natvis a PDB)
ms.date: 08/10/2017
f1_keywords:
- /natvis
helpviewer_keywords:
- NATVIS linker option
- /NATVIS linker option
- -NATVIS linker option
- Add Natvis file to PDB
ms.assetid: 8747fc0c-701a-4796-bb4d-818ab4465cca
ms.openlocfilehash: a16e320a2f8f946912fef6a354f27f6514a67e29
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439279"
---
# <a name="natvis-add-natvis-to-pdb"></a>/NATVIS (Agregar Natvis a PDB)

> /NATVIS:*nombre de archivo*

## <a name="parameters"></a>Parámetros

*filename*<br/>
Archivo Natvis que se va a agregar al archivo PDB. Inserta las visualizaciones del depurador en el archivo Natvis en la PDB.

## <a name="remarks"></a>Observaciones

La opción/NATVIS incrusta las visualizaciones del depurador definidas en el *nombre* de archivo del archivo NATVIS en el archivo PDB generado por Link. Esto permite al depurador mostrar las visualizaciones independientemente del archivo. natvis. Puede usar varias opciones de/NATVIS para insertar más de un archivo Natvis en el archivo PDB generado.

LINK omite/NATVIS cuando no se crea un archivo PDB mediante una opción [/Debug](debug-generate-debug-info.md) . Para obtener información sobre la creación y el uso de archivos. natvis, vea [crear vistas personalizadas de objetos nativos en el depurador de Visual Studio](/visualstudio/debugger/create-custom-views-of-native-objects).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades **línea de comandos** en la carpeta **vinculador** .

1. Agregue la opción/NATVIS al cuadro de texto **opciones adicionales** .

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Esta opción no tiene un equivalente de programación.

## <a name="see-also"></a>Consulte también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
