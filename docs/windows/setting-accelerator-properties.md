---
title: Establecer propiedades de acelerador (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
- VIRTKEY
- Key property
- ID property
ms.assetid: 0fce9156-3025-4e18-b034-e219a4c65812
ms.openlocfilehash: e1fac31635b7ccc09f9c184cf734fa4f7717cb97
ms.sourcegitcommit: 5beace7dcc6bf0e8b8cc96a930e7424f9daa05cb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2019
ms.locfileid: "55232141"
---
# <a name="setting-accelerator-properties"></a>Establecer propiedades de Acelerador

Puede establecer propiedades de acelerador el [ventana propiedades](/visualstudio/ide/reference/properties-window) en cualquier momento. También puede usar el [editor de aceleradores](../windows/accelerator-editor.md) para modificar las propiedades de Acelerador de la tabla de aceleradores. Los cambios realizados mediante el **propiedades** ventana o el **acelerador** editor tiene el mismo resultado: las modificaciones se reflejan inmediatamente en la tabla de aceleradores.

## <a name="id-property"></a>ID (propiedad)

El **ID** propiedad hace referencia a cada entrada de la tabla de aceleradores en código de programa. Esta entrada es el valor del comando que va a recibir el programa cuando un usuario presiona la tecla de aceleración o una combinación de teclas. Para realizar un acelerador igual que un elemento de menú, realice sus identificadores de la misma (siempre y cuando el identificador de la tabla de aceleradores es el mismo que el identificador para el recurso de menú).

Hay tres propiedades para cada Id. de acelerador: el **modificador** propiedad, el **clave** propiedad y el **tipo** propiedad.

## <a name="modifier-property"></a>Modifier (propiedad)

El **modificador** propiedad establece el control de combinaciones de teclas para el acelerador.

> [!NOTE]
> En el **propiedades** ventana, esta propiedad aparece como tres independiente **booleano** propiedades, que puede controlarse de forma independiente: **ALT**, **Ctrl**, y **MAYÚS**.

Los siguientes son entradas legales para el **modificador** propiedad en la tabla de aceleradores:

   |Valor|Descripción|
   |-----------|-----------------|
   |**Ninguno**|Usuario presiona sólo el **clave** valor. Este valor se utiliza la forma más eficaz con los valores ASCII/ANSI 001 a 026, que se interpreta como ^ A ^ Z (**CTRL+a** a través de **CTRL+z**).|
   |**Alt**|El usuario debe presionar el **Alt** clave antes de la **clave** valor.|
   |**Ctrl**|El usuario debe presionar el **Ctrl** clave antes de la **clave** valor. No es válido con el tipo de ASCII.|
   |**Mayús**|El usuario debe presionar el **MAYÚS** clave antes de la **clave** valor.|
   |**Ctrl+Alt**|El usuario debe presionar el **Ctrl** clave y el **Alt** clave antes de la **clave** valor. No es válido con el tipo de ASCII.|
   |**CTRL + MAYÚS**|El usuario debe presionar el **Ctrl** clave y el **MAYÚS** clave antes de la **clave** valor. No es válido con el tipo de ASCII.|
   |**ALT + MAYÚS**|El usuario debe presionar el **Alt** clave y el **MAYÚS** clave antes de la **clave** valor. No es válido con el tipo de ASCII.|
   |**Ctrl + Alt + Mayús**|El usuario debe presionar **Ctrl**, **Alt**, y **MAYÚS** antes de la **clave** valor. No es válido con el tipo de ASCII.|

## <a name="key-property"></a>Key (propiedad)

El **clave** propiedad establece la clave real que se usará como el acelerador.

Los siguientes son entradas legales para el **clave** propiedad en la tabla de aceleradores:

   |Valor|Descripción|
   |-----------|-----------------|
   |Un entero entre 0 y 255 en formato decimal.|El valor determina si el valor se trata como ASCII o ANSI como sigue:<br/><br/>-Números de dígito siempre se interpretan como la clave correspondiente, en lugar de como valores ASCII o ANSI.<br/>-Los valores de 1 a 26, si van precedidos de ceros, se interpretan como ^ A ^ Z, que representa el valor ASCII de las letras del alfabeto cuando se presiona con la **Ctrl** clave se mantiene presionada.<br/>-Valores 27-32 siempre se interpretan como valores de tres dígitos decimales comprendidos entre 032 027.<br/>-Los valores de 033 a 255, ya sea precedido de 0 o no se interpretan como valores ANSI.|
   |Un carácter único teclado.|Mayúscula A - Z o los números 0 - 9 pueden ser ASCII o valores de clave virtuales; cualquier otro carácter solo es ASCII.|
   |Un carácter único teclado en el intervalo A - Z (sólo mayúsculas), precedida por un símbolo de intercalación (^) (por ejemplo, ^ C).|Esta opción especifica el valor de ASCII de la clave cuando se presiona con la **Ctrl** tecla presionada.|
   |Cualquier identificador de clave virtual válido.|El cuadro de lista desplegable clave en la tabla de aceleradores contiene una lista de identificadores de clave virtuales estándares.|

> [!NOTE]
> Cuando escribe un valor ASCII, las opciones de la propiedad modificador son limitadas. La única clave de control disponible para su uso es la **Alt** clave.

> [!TIP]
> Es otra manera de definir una tecla de aceleración para el botón derecho en una o varias entradas en la tabla de aceleradores, elija **tecla siguiente** en el menú contextual y, a continuación, presione cualquiera de las claves o combinaciones de teclas del teclado. El **tecla siguiente** comando también está disponible desde el **editar** menú.

## <a name="type-property"></a>Type (propiedad)

El **tipo** propiedad determina si la combinación de teclas de método abreviado asociada con el Id. de acelerador se interpreta como un valor de clave ASCII/ANSI o una combinación de tecla virtual (VIRTKEY).

- Si el **tipo** propiedad es ASCII, el **modificador** sólo puede ser propiedad `None` o `Alt`, o puede tener un acelerador que usa el **Ctrl** clave () anteponer a la clave con un `^`).

- Si el **tipo** propiedad es VIRTKEY, cualquier combinación de `Modifier` y `Key` valores es válido.

> [!NOTE]
> Si desea especificar un valor en la tabla de aceleradores y tienen el valor se tratan como ASCII/ANSI, simplemente haga clic en el **tipo** para la entrada en la tabla y seleccione ASCII en la lista desplegable. Sin embargo, si usa el **tecla siguiente** comando (**editar** menú) para especificar el `Key`, debe cambiar la **tipo** propiedad de VIRTKEY a ASCII *antes* escribir el `Key` código.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Edición en una tabla de aceleradores](../windows/editing-in-an-accelerator-table.md)<br/>
[Teclas de aceleración predefinidas](../windows/predefined-accelerator-keys.md)<br/>
[Editores de recursos](../windows/resource-editors.md)<br/>
