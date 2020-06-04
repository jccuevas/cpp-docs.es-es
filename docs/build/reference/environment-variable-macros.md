---
title: Macros de variables de entorno
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, environment variable macros
- environment variables, macros in NMAKE
- macros, environment-variable
ms.assetid: f8e96635-0906-47b0-9f56-12a6fdf5e347
ms.openlocfilehash: a96b2de8469ace971d7fbc2707d3f786e873bb26
ms.sourcegitcommit: 6cb0670ca7d40e8ec55f162b8ce2847f5ae15f5c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67787340"
---
# <a name="environment-variable-macros"></a>Macros de variables de entorno

NMAKE hereda las definiciones de macro para variables de entorno que existían antes del inicio de la sesión. Si una variable se establece en el entorno del sistema operativo, está disponible como una macro NMAKE. Los nombres heredados se convierten a mayúsculas. Herencia tiene lugar antes de preprocesamiento. Use la opción /E para hacer que las macros heredadas de variables de entorno para invalidar las macros con el mismo nombre en el archivo MAKE.

Macros de variables de entorno pueden redefinirse en la sesión, y esto cambia la variable de entorno correspondiente. También puede cambiar las variables de entorno con el comando. Uso del comando SET para cambiar una variable de entorno en una sesión no cambia la macro correspondiente, sin embargo.

Por ejemplo:

```
PATH=$(PATH);\nonesuch

all:
    echo %%PATH%%
```

En este ejemplo, cambiar `PATH` cambia la variable de entorno correspondiente `PATH`; lo anexa `\nonesuch` a la ruta de acceso.

Si una variable de entorno se define como una cadena que sería sintaxis incorrecta en un archivo MAKE, se crea ninguna macro y no se genera ninguna advertencia. Si el valor de la variable contiene un signo de dólar ($), NMAKE lo interpreta como el principio de una llamada de macro. Mediante la macro puede provocar un comportamiento inesperado.

## <a name="see-also"></a>Vea también

[Macros NMAKE especiales](special-nmake-macros.md)
