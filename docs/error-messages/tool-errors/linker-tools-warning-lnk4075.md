---
title: Advertencia de las herramientas del vinculador LNK4075
ms.date: 11/04/2016
f1_keywords:
- LNK4075
helpviewer_keywords:
- LNK4075
ms.assetid: f39ad3f9-c263-4cf0-9d70-259fc56ac96d
ms.openlocfilehash: e4a385b9559e2f54e81bda76e6dd13505e978a74
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183493"
---
# <a name="linker-tools-warning-lnk4075"></a>Advertencia de las herramientas del vinculador LNK4075

se omite "Opción1" debido a la especificación "opción2"

La segunda opción invalida la primera.

Se están especificando las opciones del vinculador mutuamente excluyentes.  Examine las opciones del vinculador.  La ubicación en la que se especifiquen las opciones del vinculador depende de cómo esté compilando el proyecto.

- Si va a compilar en el entorno de desarrollo, busque en las páginas de propiedades del enlazador del proyecto y compruebe dónde se especifican ambas opciones del enlazador.  Vea [establecer las propiedades del compilador y compilación](../../build/working-with-project-properties.md) para obtener más información.

- Si compila en la línea de comandos, examine las opciones del enlazador especificadas allí.

- Si compila con scripts de compilación, examine los scripts para ver dónde se especifican estas opciones del vinculador.

Cuando encuentre dónde se especifican las opciones del vinculador mutuamente excluyentes, quite una de las opciones del enlazador.

Algunos ejemplos específicos:

- Si vincula un módulo que se compiló con **/Zi**, lo que implica una opción de vinculador interna denominada/EDITANDCONTINUE y un módulo que se compiló con/OPT: Ref,/opt: ICF o/incremental: no, lo que implica que no hay/EDITANDCONTINUE, obtendrá LNK4075.  Vea [/Z7,/Zi,/Zi (formato de la información de depuración)](../../build/reference/z7-zi-zi-debug-information-format.md) para obtener más información.
