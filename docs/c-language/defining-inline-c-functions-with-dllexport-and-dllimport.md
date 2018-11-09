---
title: Definir funciones insertadas de C con dllexport y dllimport
ms.date: 11/04/2016
helpviewer_keywords:
- inline functions [C++], with dllexport and dllimport
- dllimport attribute [C++], inline functions
- dllexport attribute [C++], inline functions
- dllexport attribute [C++]
ms.assetid: 41418f7c-1c11-470b-bb2e-1f8269a239f0
ms.openlocfilehash: 386049b5dcf279290025dd367710465d4c03f587
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610618"
---
# <a name="defining-inline-c-functions-with-dllexport-and-dllimport"></a>Definir funciones insertadas de C con dllexport y dllimport

**Específicos de Microsoft**

Puede definir como alineada una función con el atributo `dllexport`. En este caso, siempre se crean instancias de la función, y siempre se exporta, independientemente de si un módulo del programa hace referencia o no a la función. Se supone que otro programa importa la función.

También puede definir como alineada una función declarada con el atributo **dllimport**. En este caso, la función puede expandirse (de acuerdo con la especificación de opción del compilador /Ob (inline)), pero no puede crearse una instancia de ella. En concreto, si se toma la dirección de una función alineada importada, se devuelve la dirección de la función que reside en la DLL. Este comportamiento es el mismo que cuando se toma la dirección de una función importada no alineada.

Los datos y cadenas locales estáticos en funciones inline mantienen las mismas identidades entre la DLL y el cliente que mantendrían en un solo programa (es decir, un archivo ejecutable sin una interfaz DLL).

Tome precauciones cuando proporcione funciones insertadas importadas. Por ejemplo, si actualiza la DLL, no suponga que el cliente utilizará la versión modificada de la DLL. Para asegurarse de que se carga la versión correcta, recompile el cliente de DLL también.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Funciones de importación y exportación de archivos DLL](../c-language/dll-import-and-export-functions.md)