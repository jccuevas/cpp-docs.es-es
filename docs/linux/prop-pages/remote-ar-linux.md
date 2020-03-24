---
title: Propiedades de archivo remoto (C++ para Linux)
ms.date: 06/07/2019
ms.assetid: 5ee1e44c-8337-4c3a-b2f3-35e4be954f9f
f1_keywords: []
ms.openlocfilehash: dc20eecef9947581ca87b9489285bc058a249e26
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446817"
---
# <a name="remote-archive-properties-c-linux"></a>Propiedades de archivo remoto (C++ para Linux)

::: moniker range="vs-2015"

La compatibilidad con Linux está disponible en Visual Studio 2017 y versiones posteriores.

::: moniker-end

::: moniker range=">=vs-2017"

| Propiedad. | Descripción |
|--|--|
| Crear un índice del archivo | Se crea un índice de archivo (tal y como lo hace ranlib). Esta opción puede acelerar la vinculación y reducir la dependencia en su propia biblioteca. |
| Crear archivo fino | Crear un archivo fino.  Un archivo fino contiene las rutas de acceso relativas a los objetos, en lugar de insertar los objetos.  Para cambiar entre Fino y Normal es necesario eliminar la biblioteca existente. |
| Sin advertencia al crear | No se muestran advertencias cuando la biblioteca se crea. |
| Truncar marca de tiempo | Usar cero para marcas de tiempo e identificadores UID/GUID. |
| Suprimir la pancarta de inicio | No se muestra el número de versión. |
| Detallado | Detallado |
| Opciones adicionales | Opciones adicionales. |
| Archivo de salida | La opción /OUT invalida el nombre y la ubicación predeterminados del programa que crea lib. |
| Archivador | Especifica el programa que debe invocarse durante la vinculación de objetos estáticos, o bien la ruta de acceso al archivador en el sistema remoto. |
| Tiempo de espera del archivador | Tiempo de espera del archivador remoto, en milisegundos. |
| Copiar salida | Especifica si debe copiarse en la máquina local el archivo de salida de compilación del sistema remoto. |

::: moniker-end
