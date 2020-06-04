---
title: Utilizar bibliotecas de importación y archivos de exportación
ms.date: 11/04/2016
helpviewer_keywords:
- circular exports
- import libraries, using
- export files
ms.assetid: 2634256a-8aa5-4495-8c9e-6cde10e4ed76
ms.openlocfilehash: 030b792d4bbebecef9d9303238657a564a142ecf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317788"
---
# <a name="using-an-import-library-and-export-file"></a>Utilizar bibliotecas de importación y archivos de exportación

Cuando un programa (un archivo ejecutable o un archivo DLL) se exporta a otro programa que importa de o, si más de dos programas exportan e importan entre sí, los comandos para vincular estos programas deben dar cabida a exportaciones circulares.

En una situación sin exportaciones circulares, al vincular un programa que utiliza exportaciones desde otro programa, debe especificar la biblioteca de importación para el programa exportador. La biblioteca de importación para el programa de exportación se crea cuando se vincula dicho programa. Por lo tanto, debe vincular el programa exportador antes de que el programa de importación. Por ejemplo, si dos.dll importa desde uno.dll, primero debe vincular ONE.dll y obtener la biblioteca de importación ONE.lib. A continuación, especifica uno.lib al vincular dos.dll. Cuando el vinculador crea dos.dll, también crea su biblioteca de importación, dos.lib. Utilice dos.lib al vincular programas que importe desde TWO.dll.

Sin embargo, en una situación de exportación circular, no es posible vincular todos los programas interdependientes mediante bibliotecas de importación de otros programas. En el ejemplo expuesto anteriormente, si dos.dll también exporta a uno.dll, la biblioteca de importación para dos.dll no existirá aún cuando se vincule uno.dll. Cuando existan exportaciones circulares, deberá utilizar LIB para crear una biblioteca de importación y exportación de archivo para uno de los programas.

Para empezar, elija uno de los programas en el que se va a ejecutar LIB. En el comando LIB, enumerar todos los objetos y bibliotecas para el programa y especifique/def. Si el programa usa un archivo .def o especificaciones/Export, deberá especificarlos también.

Después de crear la biblioteca de importación (.lib) y el archivo de exportación (.exp) para el programa, use la biblioteca de importación al vincular el otro programa o programas. VÍNCULO crea una biblioteca de importación para cada programa exportador que genere. Por ejemplo, si ejecuta LIB en los objetos y las exportaciones para ONE.dll, crear ONE.lib y ONE.exp. Ahora puede usar uno.lib al vincular dos.dll; Este paso también crea la biblioteca de importación dos.lib.

Por último, vincule el programa con el que empezó. En el comando de vínculo, especifique los objetos y bibliotecas para el programa, el archivo .exp que creó LIB para el programa y la biblioteca de importación o bibliotecas para las exportaciones usadas por el programa. Para continuar con el ejemplo, el comando LINK para ONE.dll contiene ONE.exp y TWO.lib, así como los objetos y las bibliotecas en uno.dll. El comando de vínculo; no especifique el archivo .def o especificaciones/Export estos no son necesarios, porque las definiciones de exportación se encuentran en el archivo .exp. Cuando se vincula con un archivo .exp, LINK no crea una biblioteca de importación, porque se da por supuesto que uno se creó cuando creó el archivo .exp.

## <a name="see-also"></a>Vea también

[Trabajar con bibliotecas de importación y archivos de exportación](working-with-import-libraries-and-export-files.md)
