---
title: Filtrar Administrar los símbolos
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.changing
- vc.editors.symbol.restrictions.name
- vc.editors.symbol.changing.value
- vc.editors.symbol.restrictions.value
- vc.editors.symbol.changing.header
- vc.editors.symbol.changing.unassigned
- vc.editors.symbol.shared.calculated
helpviewer_keywords:
- symbol names
- symbols [C++], names
- restrictions, symbol names
- numeric values
- symbols [C++], numeric values
- numeric values, changing symbols
- symbols [C++], value restrictions
- restrictions, symbol values
- resource files [C++], multiple
- Resource Includes dialog box [C++]
- symbol header files [C++], changing names
- symbols [C++], symbol header files
- Resource.h
- symbols [C++], unassigned
- Change Symbol dialog box [C++]
- unassigned symbols
- symbols [C++], deleting
- symbols [C++], read-only
- symbols [C++], shared
- symbols [C++], calculated
- read-only symbols
- symbol directives
- calculated symbols
- shared symbols
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
ms.openlocfilehash: 4bc0376b6b5ff402f0cc9f40093e000763ad6656
ms.sourcegitcommit: bec1480a03e7b4070b469a6c131a69f516bbac70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/13/2019
ms.locfileid: "56226376"
---
# <a name="how-to-manage-symbols"></a>Filtrar Administrar los símbolos

Cuando se crea un nuevo recurso u objeto de recurso, el entorno de desarrollo le asigna un nombre de símbolo predeterminado, por ejemplo, IDD_DIALOG1. Puede usar el [ventana propiedades](/visualstudio/ide/reference/properties-window) para cambiar el nombre del símbolo predeterminado o para cambiar el nombre de cualquier símbolo ya asociado a un recurso.

Para los símbolos asociados a un único recurso, también puede usar el **propiedades** ventana para cambiar el valor de símbolo. Puede usar el [cuadro de diálogo símbolos de recursos](../windows/resource-symbols-dialog-box.md) para cambiar el valor de los símbolos no estén asignados a un recurso.

Normalmente todos los símbolos se guardan las definiciones en `Resource.h`. Sin embargo, puede que necesite cambiar este nombre de archivo de inclusión para, por ejemplo, poder trabajar con más de un archivo de recursos en el mismo directorio.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*.

> [!NOTE]
> Si el proyecto no contuviera un archivo .rc, vea [crear un nuevo archivo de Script de recursos](../windows/how-to-create-a-resource-script-file.md).

## <a name="symbol-name-restrictions"></a>Restricciones de nombre de símbolo

Las restricciones en los nombres de símbolos son las siguientes:

- Todos los [símbolos](../windows/symbols-resource-identifiers.md) debe ser único dentro del ámbito de la aplicación. Esto evita conflictos de definiciones de símbolos en los archivos de encabezado.

- Los caracteres válidos en un nombre de símbolo son A-z, a-z, 0-9 y caracteres de subrayado (_).

- Los nombres de símbolo no pueden empezar con un número y se limitan a 247 caracteres.

- Los nombres de símbolo no pueden contener espacios.

- Los nombres de símbolo no distinguen mayúsculas y minúsculas, pero se conserva el caso de la primera definición de símbolos. El compilador/editor de recursos y los programas de C++  usan el archivo de encabezado que define los símbolos para hacer referencia a los recursos definidos en un archivo de recursos. Cuando dos nombres de símbolo difieren únicamente en sus mayúsculas o minúsculas, el programa de C++ verá dos símbolos distintos, mientras que el compilador/editor de recursos verá dos nombres se remiten al mismo símbolo.

   > [!NOTE]
   > Si no respeta el esquema de nombre de símbolo estándar (ID*_[palabra clave]) descrito aquí y el nombre del símbolo resulta ser el mismo que una palabra clave conocida por el compilador de script de recursos, cuando trate de generar el archivo de script de recursos, se producirá un error aparentemente aleatorio difícil de diagnosticar. Para evitar esto, aténgase al esquema de nomenclatura estándar.

Los nombres de símbolo tienen prefijos descriptivos que indican el tipo de recurso u objeto que representan. Estos prefijos descriptivos comienzan por el identificador de combinación de texto. La biblioteca MFC (Microsoft Foundation Class) usa las convenciones de nomenclatura de símbolo recogidas en la siguiente tabla.

|Categoría|Prefijo|Usar|
|--------------|------------|---------|
|Recursos|IDR_ IDD_ IDC_ IDI_ IDB_|Acelerador o menú (y recursos asociados o personalizados) Cuadro de diálogo Cursor Icono Mapa de bits|
|Elementos de menú|ID_|Elemento de menú|
|Comandos|ID_|Comando|
|Controles y ventanas secundarias|IDC_|Control|
|Cadenas|IDS_|Cadena en la tabla de cadenas|
|MFC|AFX_|Reservado para símbolos de MFC predefinidos|

### <a name="to-change-a-symbol-name-id"></a>Para cambiar un nombre de símbolo (Id.)

1. En [vista de recursos](../windows/resource-view-window.md), seleccione el recurso.

1. En el **propiedades** ventana, escriba un nombre de símbolo nuevo o seleccione en la lista de símbolos existentes en el **ID** cuadro.

   Si escribe un nombre de símbolo nuevo, se le asigna automáticamente un valor.

Puede usar el [cuadro de diálogo símbolos de recursos](../windows/resource-symbols-dialog-box.md) para cambiar los nombres de los símbolos no estén asignados a un recurso.

## <a name="symbol-value-restrictions"></a>Restricciones de valor de símbolo

Un valor de símbolo puede ser cualquier entero expresado de la forma normal para las directivas de preprocesador #define. A continuación se muestran algunos ejemplos de valores de símbolo:

```
18
4001
0x0012
-3456
```

Los valores de símbolo de recursos (aceleradores, mapas de bits, cursores, cuadros de diálogo, iconos, menús, tablas de cadenas e información de versión) deben ser números decimales comprendidos en el intervalo de 0 a 32.767 (pero no pueden ser hexadecimales). Los valores de símbolo de partes de recursos, como los controles de cuadro de diálogo o las cadenas individuales de la tabla de cadenas, pueden ir de 0 a 65.534 o de -32.768 a 32.767.

Símbolos de recursos son números de 16 bits. Puede especificarlos con o sin signo, sin embargo, se usan internamente como enteros sin signo. Así pues, los números negativos se convertirán a su valor positivo correspondiente.

A continuación se muestran algunas limitaciones de los valores de símbolo:

- El entorno de desarrollo de Visual Studio y MFC usan algunos intervalos numéricos para fines especiales. MFC se reserva todos los números con el bit más significativo establecido (de -32.768 a -1 o de 32.768 a 65.534, en función del signo).

- No se puede definir un valor de símbolo usando otras cadenas de símbolo. Por ejemplo, no se admite la definición de símbolos siguientes:

    ```cpp
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported
    ```

- No se puede usar macros de preprocesador con argumentos como definiciones de valor. Por ejemplo:

    ```cpp
    #define   IDD_ABOUT  ID(7) //not supported
    ```

   no es una expresión válida, independientemente de cómo `ID` se evalúa como el tiempo de compilación.

- La aplicación puede tener un archivo que contenga símbolos definidos con expresiones. Para obtener más información sobre cómo incluir los símbolos como símbolos de solo lectura, consulte [símbolos utilizando compartidos (de solo lectura) o calculados](../windows/including-shared-read-only-or-calculated-symbols.md).

Para obtener más información sobre los intervalos numéricos, vea [TN023: Recursos de MFC estándar](../mfc/tn023-standard-mfc-resources.md).

### <a name="to-change-a-symbol-value"></a>Para cambiar un valor de símbolo

1. En [vista de recursos](../windows/resource-view-window.md), seleccione el recurso.

1. En el **propiedades** ventana, escriba el nombre del símbolo seguido por un signo igual y un número entero en el **ID** cuadro, por ejemplo:

    ```
    IDC_EDITNAME=5100
    ```

El nuevo valor se almacena en el archivo de encabezado de símbolos la próxima vez que guarde el proyecto. Solo el nombre del símbolo permanece visible en el cuadro de identificador. el signo igual y el valor no se muestran después de que va a validar.

## <a name="change-or-delete-unassigned-symbols"></a>Cambiar o eliminar símbolos sin asignar

Mientras se encuentre en el [cuadro de diálogo símbolos de recursos](../windows/resource-symbols-dialog-box.md), puede editar o eliminar símbolos existentes que ya no están asignados a un recurso u objeto.

### <a name="to-change-an-unassigned-symbol"></a>Para cambiar un símbolo sin asignar

1. En el **nombre** cuadro, seleccione el símbolo sin asignar y elija **cambio**.

1. Editar nombre o un valor en los cuadros correspondientes en el símbolo del **cambiar símbolo** cuadro de diálogo.

   > [!NOTE]
   > Para cambiar un símbolo que *es* asignado a un recurso u objeto, debe usar el editor de recursos o **propiedades** ventana.

### <a name="to-delete-an-unassigned-unused-symbol"></a>Para eliminar un símbolo sin asignar (sin usar)

En el [cuadro de diálogo símbolos de recursos](../windows/resource-symbols-dialog-box.md), seleccione el símbolo que desea eliminar y elija **eliminar**.

   > [!NOTE]
   > Antes de eliminar un símbolo sin usar en un archivo de recursos, asegúrese de que no se usa en ninguna otra parte del programa o en archivos de recursos incluidos en el tiempo de compilación.

## <a name="include-shared-read-only-or-calculated-symbols"></a>Incluir compartidos (de sólo lectura) o calculados símbolos

La primera vez que el entorno de desarrollo lee un archivo de recursos creado por otra aplicación, marca todos los archivos de encabezado incluidos como de solo lectura. Aunque puede usar el [incluye recursos de cuadro de diálogo](../windows/resource-includes-dialog-box.md) para agregar archivos de encabezado de símbolos de solo lectura adicionales.

Tal vez le interese usar definiciones de símbolos de solo lectura para los archivos de símbolos que desea compartir entre varios proyectos.

También puede usar los archivos de símbolos incluidos cuando dispone de recursos existentes con definiciones de símbolos que usan expresiones en lugar de enteros sencillos para definir el valor de símbolo. Por ejemplo:

```cpp
#define   IDC_CONTROL1 2100
#define   IDC_CONTROL2 (IDC_CONTROL1+1)
```

El entorno interpreta correctamente estos símbolos calculados siempre y cuando:

- Los símbolos calculados se coloquen en un archivo de símbolos de solo lectura.

- El archivo de recursos contenga recursos a los que ya están asignados estos símbolos calculados.

- Se espere una expresión numérica.

> [!NOTE]
> Si se espera una cadena o una expresión numérica, la expresión no se evalúa.

### <a name="to-include-shared-read-only-symbols-in-your-resource-file"></a>Para incluir símbolos compartidos (de solo lectura) en el archivo de recursos

1. En [vista de recursos](../windows/resource-view-window.md), haga clic en el archivo .rc y elija [incluye recursos](../windows/resource-includes-dialog-box.md) en el menú contextual.

1. En el **directivas de símbolos de solo lectura** cuadro, use el `#include` directiva de compilador para especificar el archivo donde desea que se conserven los símbolos de solo lectura.

   No llame a los archivos `Resource.h`, ya que es el nombre de archivo usada normalmente en el archivo de encabezado de símbolos principal.

   > [!NOTE]
   > **Importante** lo que escribe en el cuadro directivas de símbolos de solo lectura se incluye en el archivo de recursos exactamente como se escribe. Asegúrese de que lo que escribe no contiene errores de sintaxis o de ortografía.

   Use la **directivas de símbolos de solo lectura** casilla para incluir los archivos con las definiciones de símbolos. No incluya definiciones de recursos; en caso contrario, se crearán definiciones de recursos duplicadas cuando se guarda el archivo.

1. Coloque los símbolos en el archivo especificado.

   Los símbolos de los archivos incluidos de esta manera se evalúan cada vez que abra el archivo de recursos, pero no se reemplazan en el disco cuando guarde el archivo.

1. Seleccione **Aceptar**.

### <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>Para cambiar el nombre del archivo de encabezado de símbolos de recurso

1. En [vista de recursos](../windows/resource-view-window.md), haga clic en el archivo .rc y elija [incluye recursos](../windows/resource-includes-dialog-box.md) en el menú contextual.

1. En el **archivo de encabezado de símbolos** , escriba el nuevo nombre del archivo de inclusión.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Símbolos: Identificadores de recursos](../windows/symbols-resource-identifiers.md)<br/>
[Identificadores de símbolo predefinidos](../windows/predefined-symbol-ids.md)<br/>
[Visualización de símbolos de recursos](../windows/viewing-resource-symbols.md)<br/>