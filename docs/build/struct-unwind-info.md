---
title: UNWIND_INFO (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f0aee906-a1b9-44cc-a8ad-463637bd5411
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 14b17a79905ffc7814e2aecf92e90f3db526453f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="struct-unwindinfo"></a>UNWIND_INFO (Estructura)
La estructura de información de datos de desenredo sirve para registrar los efectos de una función en el puntero de pila y donde se guardan los registros no volátiles en la pila:  
  
|||  
|-|-|  
|UBYTE: 3|Versión|  
|UBYTE: 5|Marcas|  
|UBYTE|Tamaño de prólogo|  
|UBYTE|Recuento de códigos de desenredado|  
|UBYTE: 4|Registro de marco|  
|UBYTE: 4|Desplazamiento de fotogramas Register (escalada)|  
|USHORT * n|Matriz de códigos de desenredado|  
|variable|Puede tener formato (1) o (2) a continuación|  
  
 (1) controlador de excepciones  
  
|||  
|-|-|  
|ULONG|Dirección del controlador de excepciones|  
|variable|Datos del controlador específicos del lenguaje (opcionales)|  
  
 (2) encadenadas de información de desenredo  
  
|||  
|-|-|  
|ULONG|Dirección de inicio (función)|  
|ULONG|Dirección final (función)|  
|ULONG|Dirección de información de desenredo|  
  
 La estructura UNWIND_INFO debe ser DWORD alineada en memoria. El significado de cada campo es el siguiente:  
  
 **Versión**  
 Número de versión de los datos de desenredo, actualmente 1.  
  
 **Marcas**  
 Actualmente se definen tres indicadores:  
  
 UNW_FLAG_EHANDLER la función tiene un controlador de excepciones que debe llamarse al buscar las funciones que necesitan para examinar las excepciones.  
  
 UNW_FLAG_UHANDLER la función tiene un controlador de terminación que se debe llamar cuando se desenrede una excepción.  
  
 UNW_FLAG_CHAININFO Esta estructura no es el principal para el procedimiento de información de desenredo. En su lugar, la información de desenredo encadenada entrada es el contenido de una entrada RUNTIME_FUNCTION anterior. Ver el texto siguiente para obtener una explicación de encadenadas estructuras de información de desenredo. Si se establece esta marca, los indicadores UNW_FLAG_EHANDLER y UNW_FLAG_UHANDLER deben borrarse. Además, los campos de asignación de registro y de pila fija de marco deben tener los mismos valores que en el servidor principal de información de desenredo.  
  
 **Tamaño de prólogo**  
 Longitud del prólogo de función en bytes.  
  
 **Recuento de códigos de desenredado**  
 Este es el número de ranuras de la matriz de códigos de desenredado. Tenga en cuenta que algunos códigos de desenredado con (por ejemplo, UWOP_SAVE_NONVOL) requieren más de una ranura en la matriz.  
  
 **Registro de marco**  
 Si es distinto de cero, a continuación, la función utiliza un puntero de marco y este campo es el número del registro no volátil usa como puntero de marco, con la misma codificación para el campo de información de la operación de nodos UNWIND_CODE.  
  
 **Marco registrar desplazamiento (escala)**  
 Si el campo de registro de marco es distinto de cero, es el desplazamiento de RSP que se aplica al registro de FP cuando se estableció la escalado. El registro de FP real se establece en RSP + 16 * este número, permitiendo desplazamientos de 0 a 240. Esto permite que señala el registro de FP al centro de la asignación local de la pila para marcos de pila dinámicos, lo que permite una mejor densidad del código a través de instrucciones más breves (más instrucciones pueden usar la forma de desplazamiento de 8 bits con signo).  
  
 **Matriz de códigos de desenredado**  
 Se trata de una matriz de elementos que explica el efecto del prólogo en los registros no volátiles y RSP. Vea la sección sobre UNWIND_CODE para los significados de elementos individuales. Para la alineación, esta matriz siempre tendrá un número par de entradas, con la última entrada potencialmente sin utilizar (en cuyo caso la matriz será uno mayor que el indicado por el recuento de campo de códigos de desenredado).  
  
 **Dirección del controlador de excepciones**  
 Se trata de un puntero de imagen relativo al controlador de terminación o de excepciones específicos del idioma de la función (si el indicador UNW_FLAG_CHAININFO está desactivado y se ha establecido uno de los indicadores UNW_FLAG_EHANDLER o UNW_FLAG_UHANDLER).  
  
 **Datos del controlador específicos del lenguaje**  
 Se trata de datos del controlador de excepción específica del lenguaje de la función. El formato de estos datos se no se especifica y totalmente determinado por el controlador de excepción específica en uso.  
  
 **Encadenadas de información de desenredo**  
 Si se establece el indicador UNW_FLAG_CHAININFO la estructura UNWIND_INFO finaliza con tres UWORD.  Estos UWORD representan la información de RUNTIME_FUNCTION para la función de desenredo encadenada.  
  
## <a name="see-also"></a>Vea también  
 [Datos de desenredo para la compatibilidad con el control de excepciones y el depurador](../build/unwind-data-for-exception-handling-debugger-support.md)