---
title: Agregar una función miembro
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.classes.member.function
- vc.codewiz.function.overview
helpviewer_keywords:
- member functions, adding to classes
- classes [C++], adding members
- add member function wizard [C++]
ms.assetid: 55b25ddb-541d-44ed-957c-974ef91cfc85
ms.openlocfilehash: 1cd7abbbc43ae56861b3b83451b41933b8b0b4f0
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693417"
---
# <a name="add-a-member-function"></a>Agregar una función miembro

En la **Vista de clases**, puede agregar una función miembro a cualquier clase. Cuando lo hace, se agrega una declaración al archivo de encabezado, así como el cuerpo de una función miembro auxiliar al archivo de implementación de la clase, que después puede modificarse.

**Para agregar una función miembro a una clase:**

1. En la **Vista de clases**, expanda el nodo del proyecto para mostrar las clases del proyecto. (Para abrir la **Vista de clases**, en la barra de menús, seleccione **Ver**, **Vista de clases**).

1. Abra el menú contextual de la clase a la que quiera agregar una función miembro y, después, seleccione **Agregar**, **Agregar función**.

1. Proporcione los detalles deseados sobre la función miembro. Para obtener más información, vea [Asistente para agregar funciones miembro](#add-member-function-wizard).

1. Haga clic en el botón **Finalizar** para generar el código de la función miembro.

## <a name="in-this-section"></a>En esta sección

- [Asistente para agregar funciones miembro](#add-member-function-wizard)

## <a name="add-member-function-wizard"></a>Asistente para agregar funciones miembro

Este asistente agrega una declaración de función miembro al archivo de encabezado. También agrega una implementación de función miembro stub al archivo de implementación de la clase seleccionada.

Una vez agregada la función miembro mediante el asistente, el código se puede modificar en el entorno de desarrollo.

- **Tipo de valor devuelto**

  Establece el tipo de valor devuelto de la función miembro que se va a agregar. Se puede proporcionar un tipo de valor devuelto propio, o bien se puede seleccionar en la lista de tipos disponibles. Para obtener información sobre los tipos, vea [Tipos fundamentales](../cpp/fundamental-types-cpp.md).

  | | | |
  |---|---|---|
  | `char` | `int` | `unsigned int` |
  | `double` | `long` | `unsigned long` |
  | `float` | `short` | `void` |
  | `HRESULT` | `unsigned char` | |

- **Nombre de la función**

  Establece el nombre de la función miembro que se va a agregar.

- **Tipo de parámetro**

  Establece el tipo de parámetro que se va a agregar para la función miembro, si esta tiene parámetros. Se puede proporcionar un tipo de parámetro propio, o bien se puede seleccionar en la lista de tipos disponibles.

  | | | |
  |---|---|---|
  | `char` | `int` | `unsigned char` |
  | `double` | `long` | `unsigned int` |
  | `float` | `short` | `unsigned long` |

- **Nombre del parámetro**

  Establece el nombre de un parámetro que se va a agregar para la función miembro, si esta tiene parámetros.

- **Lista de parámetros**

  Muestra una lista de parámetros que se han agregado a la función miembro. Para agregar un parámetro a la lista, proporcione un tipo y un nombre en los cuadros **Tipo de parámetro** y **Nombre de parámetro** y seleccione **Agregar**. Para quitar un parámetro de la lista, selecciónelo y luego seleccione **Quitar**.

- **Acceso**

  Establece el acceso a la función miembro. Los modificadores de acceso son palabras clave que especifican el acceso que tienen otras clases a la función miembro. Para obtener más información sobre la especificación de acceso, vea [Control de acceso a miembros](../cpp/member-access-control-cpp.md). El nivel de acceso de la función miembro se establece en `public` de forma predeterminada.

  - [public](../cpp/public-cpp.md)
  - [protected](../cpp/protected-cpp.md)
  - [private](../cpp/private-cpp.md)

  Compruebe si la nueva función miembro es estática o virtual, y si es alineada o pura. Si la función miembro se establece como pura, la casilla **Virtual** está activada y la casilla **Alineado** no está disponible. El valor predeterminado es una función miembro no estática y no virtual.

  | Opción | Descripción |
  |--------|-------------|
  | [Static](../cpp/storage-classes-cpp.md) |  Especifica que la función actúa como global y que se la puede llamar desde fuera de la clase, incluso sin instancia de clase. La función miembro no tiene acceso a los miembros no estáticos. Una función miembro especificada como `Static` no puede ser virtual. |
  | [Virtual](../cpp/virtual-cpp.md) | Se asegura de que se llame a la función miembro correcta para un objeto, independientemente de la expresión usada para realizar la llamada a la función miembro. Una función miembro especificada como `Virtual` no puede ser estática. |
  | **Pura** | Indica que no se proporciona ninguna implementación para la función miembro virtual que se declara. **Pura** solo se puede especificar en funciones miembro virtuales. Una clase que contiene al menos una función miembro virtual pura se considera una clase abstracta. Las clases derivadas de la clase abstracta deben implementar la función miembro virtual pura o deben ser también clases abstractas. |
  | [Alineado](../cpp/inline-functions-cpp.md) | Indica al compilador que inserte una copia del cuerpo de la función miembro en cada lugar donde se llama a la función miembro. Una función miembro especificada como **Alineado** no puede ser pura. |

- **Archivo .cpp**

  Establece la ubicación del archivo donde se escribe la implementación de la función miembro de código auxiliar. De forma predeterminada, se escribe en el archivo .cpp de la clase a la que se agrega la función miembro. Seleccione el botón de puntos suspensivos para cambiar el nombre de archivo. La implementación de la función miembro se agrega al contenido del archivo seleccionado.

- **Comentario**

  Proporciona un comentario en el archivo de encabezado para la función miembro.

- **Firma de la función**

  Muestra la función miembro textual del código al seleccionar **Finalizar**. No se puede editar el texto de este cuadro. Para cambiar la función miembro, cambie las casillas correspondientes en el asistente.
