---
title: Advertencia de las herramientas del vinculador LNK4075
ms.date: 11/04/2016
f1_keywords:
- LNK4075
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
ms.openlocfilehash: bf22e7c78dce6949c357d7ad4a0c76209c88eef3
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809904"
---
# <a name="linker-tools-warning-lnk4075"></a>Advertencia de las herramientas del vinculador LNK4075

omitiendo la opción "1" debido a la especificación "option2"

La segunda opción reemplaza la primera.

Se especifican las opciones del vinculador mutuamente excluyentes.  Examine las opciones del vinculador.  Donde se especifican las opciones del vinculador depende de cómo va a compilar el proyecto.

- Si va a compilar en el entorno de desarrollo, busque en las páginas de propiedades del enlazador para el proyecto y ver donde se especifican ambas opciones del vinculador.  Consulte [establecer compilador y las propiedades de compilación](../../build/working-with-project-properties.md) para obtener más información.

- Si compila en la línea de comandos, examine las opciones del enlazador especificadas no existe.

- Si compila con los scripts de compilación, examine las secuencias de comandos para ver dónde se especifican estas opciones del vinculador.

Cuando encuentre donde se especifican las opciones del vinculador mutuamente excluyentes, quite una de las opciones del vinculador.

Algunos ejemplos específicos:

- Si vincula un módulo que se compiló con **/Zi**, lo que implica una opción del vinculador interno llama/EDITANDCONTINUE y un módulo que se compiló con/OPT: REF, / OPT: ICF o/incremental: no, lo que no implica ningún/EDITANDCONTINUE, podrá obtener LNK4075.  Consulte [/Z7, / Zi, /ZI (formato de la información de depuración)](../../build/reference/z7-zi-zi-debug-information-format.md) para obtener más información.