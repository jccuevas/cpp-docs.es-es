---
title: Agregar funciones miembro | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.function.overview
dev_langs:
- C++
helpviewer_keywords:
- Add Member Function Wizard [C++]
ms.assetid: 13b6defc-faa6-4d57-83db-9dd854cbea3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 488c7ca455b267a79b0d2906849596346a191792
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="add-member-function-wizard"></a>Asistente para agregar funciones miembro
Este asistente agrega una declaración de función miembro para el archivo de encabezado y una implementación de función miembro de código auxiliar para el archivo de implementación para la clase seleccionada.  
  
 Cuando haya agregado la función de miembro con el asistente, puede modificar el código en el entorno de desarrollo.  
  
 **Tipo de valor devuelto**  
 Establece el tipo de valor devuelto para la función de miembro que se va a agregar. Puede proporcionar su propio tipo de valor devuelto, o puede seleccionar en la lista de tipos disponibles. Para obtener información acerca de los tipos, vea [tipos fundamentales](../cpp/fundamental-types-cpp.md).  
  
||||  
|-|-|-|  
|`char`|`int`|`unsigned int`|  
|**double**|**long**|`unsigned long`|  
|**float**|**short**|`void`|  
|`HRESULT`|`unsigned char`||  
  
 **Nombre de la función**  
 Establece el nombre de la función de miembro que se va a agregar.  
  
 **Tipo de parámetro**  
 Establece el tipo de parámetro que se va a agregar para la función miembro, si la función miembro tiene parámetros. Puede proporcionar su propio tipo de parámetro, o puede seleccionar en la lista de tipos disponibles.  
  
||||  
|-|-|-|  
|`char`|`int`|`unsigned char`|  
|**double**|**long**|`unsigned int`|  
|**float**|**short**|`unsigned long`|  
  
 **Nombre de parámetro**  
 Establece el nombre de un parámetro que se va a agregar para la función miembro, si la función miembro tiene parámetros.  
  
 **Lista de parámetros**  
 Muestra una lista de parámetros que se ha agregado a la función miembro. Para agregar un parámetro a la lista, proporcionar un tipo y el nombre de la **tipo de parámetro** y **nombre de parámetro** y haga clic en **agregar**. Para quitar un parámetro de la lista, seleccione el parámetro y haga clic en **quitar**.  
  
 **Acceso**  
 Establece el acceso a la función miembro. Modificadores de acceso son palabras clave que especifican el acceso que tienen otras clases a la función miembro. Vea [Control de acceso a miembros](../cpp/member-access-control-cpp.md) para obtener más información acerca de cómo especificar el acceso. El nivel de acceso de la función de miembro se establece en **público** de forma predeterminada.  
  
-   [public](../cpp/public-cpp.md)  
  
-   [protected](../cpp/protected-cpp.md)  
  
-   [private](../cpp/private-cpp.md)  
  
 Compruebe si la nueva función miembro es estático o virtual, y si es en línea o puro. Si establece la función miembro como pura, la `Virtual` casilla está activada y el **en línea** casilla de verificación no está disponible. El valor predeterminado es una función miembro no estática y no virtual.  
  
|Opción|Descripción|  
|------------|-----------------|  
|[Static](../cpp/storage-classes-cpp.md)|Especifica que la función actúa como global y se puede llamar fuera de la clase, incluso con ninguna instancia de clase. La función miembro no tiene acceso a los miembros no estáticos. Una función miembro especificada como `Static` no puede ser virtual.|  
|[Virtual](../cpp/virtual-cpp.md)|Garantiza que se llama a la función miembro correcto para un objeto, independientemente de la expresión usada para realizar la función miembro llamada. Una función miembro especificada como `Virtual` no pueden ser estáticos.|  
|**Puros**|Indica que no se ha proporcionado ninguna implementación para la función miembro virtual que se declara; por lo tanto, **puro** puede especificarse únicamente en las funciones miembro virtuales. Una clase que contiene al menos una función miembro virtual pura se considera una clase abstracta. Las clases que derivan de la clase abstracta deben implementar la función miembro virtual pura o, también, son las clases abstractas.|  
|[En línea](../cpp/inline-functions-cpp.md)|Indica al compilador que inserte una copia del cuerpo de la función miembro en cada lugar donde que se llama a la función miembro. Una función miembro especificada como **en línea** no puede ser puro.|  
  
 **archivo .cpp**  
 Establece la ubicación del archivo donde se escribe la implementación de la función de miembro de código auxiliar. De forma predeterminada, se escribe en el archivo .cpp para la clase a la que se agrega la función miembro. Haga clic en el botón de puntos suspensivos para cambiar el nombre de archivo. La implementación de la función miembro se agrega al contenido del archivo seleccionado.  
  
 **Comentario**  
 Proporciona un comentario en el archivo de encabezado para la función miembro.  
  
 **Firma de la función**  
 Muestra la función miembro tal como aparece en el código al hacer clic en **finalizar**. No se puede editar el texto de este cuadro. Para cambiar la función miembro, cambie las casillas correspondientes en el asistente.  
  
## <a name="see-also"></a>Vea también  
 [Agregar una función miembro](../ide/adding-a-member-function-visual-cpp.md)