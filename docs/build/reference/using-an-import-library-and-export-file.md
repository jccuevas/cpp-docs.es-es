---
title: Mediante una biblioteca de importación y el archivo de exportación | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- circular exports
- import libraries, using
- export files
ms.assetid: 2634256a-8aa5-4495-8c9e-6cde10e4ed76
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 946ef702d17762e6771bad206d0bfa682a61055e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="using-an-import-library-and-export-file"></a>Utilizar bibliotecas de importación y archivos de exportación
Cuando un programa (un archivo ejecutable o un archivo DLL) exporta a otro programa que también se importa de o, si más de dos programas tanto exportación a e importan entre sí, los comandos para vincular estos programas deberán permitir exportaciones circulares.  
  
 En una situación sin exportaciones circulares, al vincular un programa que utiliza exportaciones desde otro programa, debe especificar la biblioteca de importación para el programa exportador. La biblioteca de importación para el programa exportador se crea cuando se vincula dicho programa. Por lo tanto, debe vincular el programa exportador antes de que el programa de importación. Por ejemplo, si TWO.dll importa desde ONE.dll, primero debe vincular ONE.dll y obtener la biblioteca de importación ONE.lib. A continuación, deberá especificar uno.lib al vincular dos.dll. Cuando el vinculador crea dos.dll, también crea su biblioteca de importación, dos.lib. Utilice dos.lib al vincular programas que importen desde TWO.dll.  
  
 Sin embargo, en una situación de exportación circular, no es posible vincular todos los programas interdependientes mediante bibliotecas de importación de otros programas. En el ejemplo expuesto anteriormente, si dos.dll también exporta a uno.dll, la biblioteca de importación para dos.dll no existirá aún cuando se vincule uno.dll. Cuando existan exportaciones circulares deberá utilizar LIB para crear una biblioteca de importación y exportación de archivo de uno de los programas.  
  
 Para comenzar, elija uno de los programas en el que se va a ejecutar LIB. En el comando LIB, lista de todos los objetos y las bibliotecas para el programa y especifique/def. Si el programa utiliza un archivo .def o especificaciones/Export, deberá especificarlos también.  
  
 Después de crear la biblioteca de importación (.lib) y el archivo de exportación (.exp) para el programa, utilice la biblioteca de importación al vincular los otros programas o programas. LINK crea una biblioteca de importación para cada programa exportador que genere. Por ejemplo, si ejecuta LIB en los objetos y las exportaciones para ONE.dll, crea ONE.lib y ONE.exp. Ahora puede utilizar uno.lib al vincular dos.dll; Este paso también crea la biblioteca de importación dos.lib.  
  
 Por último, vincule el programa con el que empezó. En el comando LINK, especifique los objetos y las bibliotecas para el programa, el archivo .exp que creó LIB para el programa así como la biblioteca de importación o bibliotecas para las exportaciones utilizadas por el programa. Para continuar con el ejemplo, el comando LINK para ONE.dll contiene ONE.exp y TWO.lib, así como los objetos y las bibliotecas que corresponden a ONE.dll. No especifique el archivo .def o especificaciones/Export en el comando de LINK; estos no son necesarios, ya que las definiciones de exportación están contenidas en el archivo .exp. Cuando se vincula con un archivo .exp, LINK no crea una biblioteca de importación, porque se supone que se creó cuando se creó el archivo .exp.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con bibliotecas de importación y archivos de exportación](../../build/reference/working-with-import-libraries-and-export-files.md)