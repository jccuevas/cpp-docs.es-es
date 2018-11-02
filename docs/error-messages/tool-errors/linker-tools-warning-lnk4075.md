---
title: Advertencia de las herramientas del vinculador LNK4075
ms.date: 11/04/2016
f1_keywords:
- LNK4075
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
ms.openlocfilehash: bba0fa85a3f2590c84cbb6f78fac7e49386d35a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548257"
---
# <a name="linker-tools-warning-lnk4075"></a>Advertencia de las herramientas del vinculador LNK4075

omitiendo la opción "1" debido a la especificación "option2"

La segunda opción reemplaza la primera.

Se especifican las opciones del vinculador mutuamente excluyentes.  Examine las opciones del vinculador.  Donde se especifican las opciones del vinculador depende de cómo va a compilar el proyecto.

- Si va a compilar en el entorno de desarrollo, busque en las páginas de propiedades del enlazador para el proyecto y ver donde se especifican ambas opciones del vinculador.  Consulte [trabajar con las propiedades del proyecto](../../ide/working-with-project-properties.md) para obtener más información.

- Si compila en la línea de comandos, examine las opciones del enlazador especificadas no existe.

- Si compila con los scripts de compilación, examine las secuencias de comandos para ver dónde se especifican estas opciones del vinculador.

Cuando encuentre donde se especifican las opciones del vinculador mutuamente excluyentes, quite una de las opciones del vinculador.

Algunos ejemplos específicos:

- Si vincula un módulo que se compiló con **/Zi**, lo que implica una opción del vinculador interno llama/EDITANDCONTINUE y un módulo que se compiló con/OPT: REF, / OPT: ICF o/incremental: no, lo que no implica ningún/EDITANDCONTINUE, podrá obtener LNK4075.  Consulte [/Z7, / Zi, /ZI (formato de la información de depuración)](../../build/reference/z7-zi-zi-debug-information-format.md) para obtener más información.