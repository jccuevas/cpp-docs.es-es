---
title: Asistente para agregar funciones miembro | Microsoft Docs
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
ms.openlocfilehash: f7c9f15a7f487b6f2d948404a5877a902414b37e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710533"
---
# <a name="add-member-function-wizard"></a>Asistente para agregar funciones miembro

Este asistente agrega una declaración de función miembro al archivo de encabezado y una implementación de función miembro de código auxiliar al archivo de implementación para la clase seleccionada.  
  
Una vez agregada la función miembro mediante el asistente, el código se puede modificar en el entorno de desarrollo.  
  
- **Tipo de valor devuelto**

   Establece el tipo de valor devuelto de la función miembro que se va a agregar. Se puede proporcionar un tipo de valor devuelto propio, o bien se puede seleccionar en la lista de tipos disponibles. Para obtener información sobre los tipos, vea [Tipos fundamentales](../cpp/fundamental-types-cpp.md).  
  
   ||||  
   |-|-|-|  
   |**char**|**int**|**unsigned int**|  
   |**double**|**long**|**unsigned long**|  
   |**float**|**short**|**void**|  
   |`HRESULT`|**unsigned char**||  
  
- **Nombre de la función**

   Establece el nombre de la función miembro que se va a agregar.  
  
- **Tipo de parámetro**

   Establece el tipo de parámetro que se va a agregar para la función miembro, si la función miembro tiene parámetros. Se puede proporcionar un tipo de parámetro propio, o bien se puede seleccionar en la lista de tipos disponibles.  
  
   ||||  
   |-|-|-|  
   |**char**|**int**|**unsigned char**|  
   |**double**|**long**|**unsigned int**|  
   |**float**|**short**|**unsigned long**|  
  
- **Nombre del parámetro**

   Establece el nombre del parámetro que se va a agregar para la función miembro, si la función miembro tiene parámetros.  
  
- **Lista de parámetros**

   Muestra una lista de parámetros que se han agregado a la función miembro. Para agregar un parámetro a la lista, proporcione un tipo y un nombre en los cuadros **Tipo de parámetro** y **Nombre de parámetro**, y haga clic en **Agregar**. Para quitar un parámetro de la lista, seleccione el parámetro y haga clic en **Quitar**.  
  
- **Acceso**

   Establece el acceso a la función miembro. Los modificadores de acceso son palabras clave que especifican el acceso que tienen otras clases a la función miembro. Vea [Control de acceso a miembros](../cpp/member-access-control-cpp.md) para obtener más información sobre cómo especificar el acceso. El nivel de acceso de la función miembro se establece en **public** de forma predeterminada.  
  
   - [public](../cpp/public-cpp.md)  
  
   - [protected](../cpp/protected-cpp.md)  
  
   - [private](../cpp/private-cpp.md)  
  
   Compruebe si la función miembro nueva es estática o virtual, y si es alineada o pura. Si la función miembro se establece como pura, la casilla `Virtual` está activada y la casilla **Alineado** no está disponible. El valor predeterminado es una función miembro no estática y no virtual.  
  
   |Opción|Descripción|  
   |------------|-----------------|  
   |[Static](../cpp/storage-classes-cpp.md)|Especifica que la función actúa como global y que se puede llamar desde fuera de la clase, incluso sin creación de instancias de clase. La función miembro no tiene acceso a los miembros no estáticos. Una función miembro que se especifique como `Static` no puede ser virtual.|  
   |[Virtual](../cpp/virtual-cpp.md)|Garantiza que se llame a la función miembro correcta para un objeto, con independencia de la expresión que se usó para realizar la llamada a la función miembro. Una función miembro que se especifique como `Virtual` no puede ser estática.|  
   |**Pura**|Indica que no se ha proporcionado ninguna implementación para la función miembro virtual que se declara; por tanto, solo se puede especificar **Pura** en las funciones miembro virtuales. Una clase que contiene al menos una función miembro virtual pura se considera una clase abstracta. Las clases derivadas de la clase abstracta deben implementar la función miembro virtual pura o deben ser también clases abstractas.|  
   |[Alineado](../cpp/inline-functions-cpp.md)|Indica al compilador que inserte una copia del cuerpo de la función miembro en cada lugar donde se llama a la función miembro. Una función miembro que se especifique como **Alineado** no puede ser pura.|  
  
- **Archivo .cpp**

   Establece la ubicación del archivo donde se escribe la implementación de la función miembro de código auxiliar. De forma predeterminada, se escribe en el archivo .cpp para la clase a la que se agrega la función miembro. Haga clic en el botón de puntos suspensivos para cambiar el nombre de archivo. La implementación de la función miembro se agrega al contenido del archivo seleccionado.  
  
- **Comentario**

   Proporciona un comentario en el archivo de encabezado para la función miembro.  
  
- **Firma de la función**

   Muestra la función miembro tal y como aparece en el código al hacer clic en **Finalizar**. No se puede editar el texto de este cuadro. Para cambiar la función miembro, cambie las casillas correspondientes en el asistente.  
  
## <a name="see-also"></a>Vea también  
 [Agregar una función miembro](../ide/adding-a-member-function-visual-cpp.md)