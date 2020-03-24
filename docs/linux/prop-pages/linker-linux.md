---
title: Propiedades del enlazador (C++ para Linux)
ms.date: 06/07/2019
ms.assetid: a0243a94-8164-425b-b2fe-b84ff363d546
ms.openlocfilehash: 934e639199d663cba391c9913b067f32e5e32165
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441287"
---
# <a name="linker-properties-linux-c"></a>Propiedades del enlazador (C++ para Linux)

::: moniker range="vs-2015"

La compatibilidad con Linux está disponible en Visual Studio 2017 y versiones posteriores.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="general"></a>General

| Propiedad. | Descripción | Opciones |
|--|--|--|
| Archivo de salida | La opción invalida el nombre y la ubicación predeterminados del programa que crea el enlazador. (-o) |
| Mostrar progreso | Imprime los mensajes de progreso del enlazador. |
| Versión | La opción -version indica al enlazador que agregue un número de versión en el encabezado del ejecutable. |
| Habilitar resultado detallado | La opción -verbose indica al enlazador que genere mensajes detallados para la depuración. |
| Seguimiento | La opción --trace indica al enlazador que genere los archivos de entrada a medida que se procesen. |
| Seguir símbolos | Imprima la lista de archivos en la que aparece un símbolo. (--trace-symbol=symbol) |
| Imprimir mapa | La opción --print-map indica al enlazador que genere un mapa de vínculos. |
| Informar de referencias de símbolos sin resolver | Al habilitar esta opción se informará de referencias de símbolos sin resolver. |
| Optimizar para uso de memoria | Optimizado para el uso de memoria, ya que vuelve a leer las tablas de símbolos cuando es necesario. |
| Ruta de búsqueda de biblioteca compartida | Permite que el usuario especifique la ruta de búsqueda de la biblioteca compartida. (-rpath-link=path) |
| Directorios de bibliotecas adicionales | Permite que el usuario invalide la ruta de acceso de la biblioteca del entorno. (Carpeta -L). |
| Enlazador | Especifica el programa que debe invocarse durante la vinculación, o bien la ruta de acceso al enlazador en el sistema remoto. |
| Tiempo de espera de vinculación | Tiempo de espera de la vinculación remota, en milisegundos. |
| Copiar salida | Especifica si debe copiarse en la máquina local el archivo de salida de compilación del sistema remoto. |

## <a name="input"></a>Entrada

| Propiedad. | Descripción | Opciones |
|--|--|--|
| Omitir bibliotecas predeterminadas específicas | Especifica uno o más nombres de las bibliotecas predeterminadas que se ignorarán. (--exclude-libs lib,lib) |
| Omitir bibliotecas predeterminadas | Omite las bibliotecas predeterminadas y busca solo en las bibliotecas especificadas de forma explícita. |
| Forzar referencias de símbolo sin definir | Obliga a que los símbolos se especifiquen en el archivo de salida como no definidos. (-u symbol --undefined=symbol) |
| Dependencias de biblioteca | Esta opción permite especificar bibliotecas adicionales para agregarlas a la línea de comandos del enlazador. La biblioteca adicional se agregará al final de la línea de comandos del enlazador, con el prefijo "lib" y la extensión ".a".  (-lFILE) |
| Dependencias adicionales | Especifica elementos adicionales que se agregarán a la línea de comandos del vínculo. |

## <a name="debugging"></a>Depuración

| Propiedad. | Descripción | Opciones |
|--|--|--|
| Información del símbolo de depurador | Información del símbolo de depurador del archivo de salida. | **Incluir todos**<br>**Omitir solo información del símbolo del depurador**<br>**Omitir información de todos los símbolos**<br> |
| Nombre de archivo de asignaciones | La opción Asignar indica al enlazador que cree un archivo de asignaciones con el nombre especificado por el usuario. (-Map=) |

## <a name="advanced"></a>Avanzadas

| Propiedad. | Descripción | Opciones |
|--|--|--|
| Marcar variables como de solo lectura después de la reubicación | Esta opción marca las variables como de solo lectura después de la reubicación. |
| Habilitar enlace de función inmediata | Esta opción marca el objeto para el enlace de función inmediata. |
| No requerir pila ejecutable | Esta opción indica en la salida que no requiere una pila de ejecutable. |
| Archivo completo | El archivo completo usa todos los códigos de los orígenes y las dependencias adicionales. |

::: moniker-end
