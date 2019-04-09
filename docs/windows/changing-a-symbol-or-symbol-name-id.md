---
title: Filtrar Administrar los símbolos
ms.date: 02/14/2019
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
ms.openlocfilehash: ebf10ade734d321c5a83644110d3511e4b6c827a
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034000"
---
# <a name="how-to-manage-symbols"></a>Filtrar Administrar los símbolos

Cuando se crea un nuevo recurso u objeto de recurso, el entorno de desarrollo le asigna un nombre de símbolo predeterminado, por ejemplo, `IDD_DIALOG1`. Puede usar el [ventana propiedades](/visualstudio/ide/reference/properties-window) para cambiar el nombre del símbolo predeterminado o para cambiar el nombre de cualquier símbolo ya asociado a un recurso.

Para los símbolos asociados a un único recurso, también puede usar el **propiedades** ventana para cambiar el valor de símbolo. Puede usar el [cuadro de diálogo símbolos de recursos](../windows/resource-symbols-dialog-box.md) para cambiar el valor de los símbolos no estén asignados a un recurso.

Normalmente todos los símbolos se guardan las definiciones en `Resource.h`. Sin embargo, puede que necesite cambiar este nombre de archivo de inclusión para, por ejemplo, poder trabajar con más de un archivo de recursos en el mismo directorio.

> [!NOTE]
> Si el proyecto no contuviera un archivo .rc, vea [Cómo: Crear recursos](../windows/how-to-create-a-resource-script-file.md).

## <a name="symbol-name-restrictions"></a>Restricciones de los nombres de símbolo

Las restricciones en los nombres de símbolos son las siguientes:

- Todos los [símbolos](../windows/symbols-resource-identifiers.md) debe ser único dentro del ámbito de la aplicación para evitar que las definiciones de símbolos en conflicto en los archivos de encabezado.

- Los caracteres válidos en un nombre de símbolo son A-z, a-z, 0-9 y caracteres de subrayado (_).

- Los nombres de símbolo no pueden empezar con un número y se limitan a 247 caracteres.

- Los nombres de símbolo no pueden contener espacios.

- Los nombres de símbolo no distinguen mayúsculas y minúsculas, pero se conserva el caso de la primera definición de símbolos.

   El compilador/editor de recursos y los programas de C++  usan el archivo de encabezado que define los símbolos para hacer referencia a los recursos definidos en un archivo de recursos. Cuando dos nombres de símbolo difieren únicamente en sus mayúsculas o minúsculas, el programa de C++ verá dos símbolos distintos, mientras que el compilador/editor de recursos verá dos nombres se remiten al mismo símbolo.

> [!NOTE]
> Si no sigue el esquema de nombre de símbolo estándar (ID que se describen a continuación y el nombre del símbolo resulta ser el mismo que una palabra clave conocida por el compilador de script de recursos, intenta compilar el archivo de script de recursos, se producirá un error aparentemente aleatorio de generación que es difícil de diagnosticar. Para evitar esto, aténgase al esquema de nomenclatura estándar.

Los nombres de símbolo tienen prefijos descriptivos que indican el tipo de recurso u objeto que representan. Estos prefijos descriptivos comienzan por el identificador de combinación de texto. La biblioteca Microsoft Foundation Class (MFC) usa el símbolo que se muestra en la siguiente tabla de convenciones de nomenclatura:

|Categoría|Prefijo|Usar|
|--------------|------------|---------|
|Recursos|IDR_, IDD_, IDC_, IDI_, IDB_|Acelerador o menú (y recursos asociados o personalizados) cuadro de diálogo, el cursor, el icono, el mapa de bits|
|Elementos de menú|ID_|Elemento de menú|
|Comandos|ID_|Comando|
|Controles y ventanas secundarias|IDC_|Control|
|Cadenas|IDS_|Cadena en la tabla de cadenas|
|MFC|AFX_|Reservado para símbolos de MFC predefinidos|

### <a name="to-change-a-symbol-name-id"></a>Para cambiar un nombre de símbolo (Id.)

1. En [vista de recursos](how-to-create-a-resource-script-file.md#create-resources), seleccione el recurso.

1. En el **propiedades** ventana, escriba un nombre de símbolo nuevo o seleccione en la lista de símbolos existentes en el **ID** cuadro.

   Si escribe un nombre de símbolo nuevo, se le asigna automáticamente un valor.

> [!NOTE]
> Puede usar el [cuadro de diálogo símbolos de recursos](../windows/resource-symbols-dialog-box.md) para cambiar los nombres de los símbolos no estén asignados a un recurso.

## <a name="symbol-value-restrictions"></a>Restricciones de los valores de símbolo

Un valor de símbolo puede ser cualquier entero expresado en la forma normal para `#define` las directivas de preprocesador. A continuación se muestran algunos ejemplos de valores de símbolo:

```
18
4001
0x0012
-3456
```

Valores de símbolos de recursos como los aceleradores, mapas de bits, cursores, cuadros de diálogo, iconos, menús, tablas de cadenas y versión deben ser números decimales comprendidos en el intervalo de 0 a 32.767 de información, pero no pueden ser hexadecimal. Los valores de símbolo de partes de recursos, como los controles de cuadro de diálogo o las cadenas individuales de la tabla de cadenas, pueden ir de 0 a 65.534 o de -32.768 a 32.767. Para obtener más información sobre los intervalos numéricos, vea [TN023: Recursos de MFC estándar](../mfc/tn023-standard-mfc-resources.md).

Símbolos de recursos son números de 16 bits. Puede especificarlos con o sin signo, sin embargo, se usan internamente como enteros sin signo, por lo que los números negativos se convertirán a su valor positivo correspondiente.

Algunas limitaciones de los valores de símbolo son:

- El entorno de desarrollo de Visual Studio y MFC usan algunos intervalos numéricos para fines especiales. MFC se reserva todos los números con el bit más significativo establecido (de -32.768 a -1 o de 32.768 a 65.534, en función del signo).

- No se puede definir un valor de símbolo usando otras cadenas de símbolo. Por ejemplo, no se admite la definición de símbolos siguientes:

    ```cpp
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported
    ```

- No se puede usar macros de preprocesador con argumentos como definiciones de valor. El ejemplo siguiente no es una expresión válida, independientemente de cómo `ID` se evalúa como el tiempo de compilación:

    ```cpp
    #define   IDD_ABOUT  ID(7) //not supported
    ```

- La aplicación puede tener un archivo que contenga símbolos definidos con expresiones.

### <a name="to-change-a-symbol-value"></a>Para cambiar un valor de símbolo

1. En [vista de recursos](how-to-create-a-resource-script-file.md#create-resources), seleccione el recurso.

1. En el **propiedades** ventana, escriba el nombre del símbolo seguido por un signo igual y un número entero en el **ID** cuadro, por ejemplo:

    ```
    IDC_EDITNAME=5100
    ```

   El nuevo valor se almacena en el archivo de encabezado de símbolos la próxima vez que guarde el proyecto. Solo el nombre del símbolo permanece visible en el cuadro de identificador y el signo igual y el valor no se muestran después de que va a validar.

## <a name="change-or-delete-symbols"></a>Cambiar o eliminar símbolos

Mientras se encuentre en el [cuadro de diálogo símbolos de recursos](../windows/resource-symbols-dialog-box.md), puede editar o eliminar símbolos existentes que ya no están asignados a un recurso u objeto.

### <a name="to-change-an-unassigned-symbol"></a>Para cambiar un símbolo sin asignar

1. En el **nombre** cuadro, seleccione el símbolo sin asignar y elija **cambio**.

1. Editar nombre o un valor en los cuadros correspondientes en el símbolo del **cambiar símbolo** cuadro de diálogo.

> [!NOTE]
> Para cambiar un símbolo que se asigna a un recurso u objeto, debe usar el editor de recursos o **propiedades** ventana.

### <a name="to-delete-an-unassigned-unused-symbol"></a>Para eliminar un símbolo sin asignar (sin usar)

En el **símbolos de recursos** cuadro de diálogo, seleccione el símbolo que desea eliminar y elija **eliminar**.

> [!NOTE]
> Antes de eliminar un símbolo sin usar en un archivo de recursos, asegúrese de que no se utiliza en otro lugar en el programa o archivos de recursos incluidos en tiempo de compilación.

## <a name="include-symbols"></a>Incluir símbolos

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

1. En [vista de recursos](how-to-create-a-resource-script-file.md#create-resources), haga clic en su *.rc* de archivo y seleccione [incluye recursos](../windows/resource-includes-dialog-box.md).

1. En el **directivas de símbolos de solo lectura** cuadro, use el `#include` directiva de compilador para especificar el archivo donde desea que se conserven los símbolos de solo lectura.

   No llame a los archivos `Resource.h`, ya que es el nombre de archivo usada normalmente en el archivo de encabezado de símbolos principal.

   > [!NOTE]
   > Lo que escribe en el **directivas de símbolos de solo lectura** cuadro se incluye en el archivo de recursos exactamente como se escribe. Asegúrese de que lo que escribe no contiene errores de sintaxis o de ortografía.

   Use la **directivas de símbolos de solo lectura** casilla para incluir los archivos con las definiciones de símbolos. No incluya definiciones de recursos, las definiciones de recursos duplicados en caso contrario, se creará cuando se guarda el archivo.

1. Coloque los símbolos en el archivo especificado.

   Los símbolos de los archivos incluidos de esta manera se evalúan cada vez que abra el archivo de recursos, pero no se reemplazan en el disco cuando guarde el archivo.

1. Seleccione **Aceptar**.

### <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>Para cambiar el nombre del archivo de encabezado de símbolos de recurso

1. En [vista de recursos](how-to-create-a-resource-script-file.md#create-resources), haga clic en su *.rc* de archivo y elija [incluye recursos](../windows/resource-includes-dialog-box.md).

1. En el **archivo de encabezado de símbolos** , escriba el nuevo nombre del archivo de inclusión.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Identificadores de recursos (símbolos)](../windows/symbols-resource-identifiers.md)<br/>
[Filtrar Creación de símbolos](../windows/creating-new-symbols.md)<br/>
[Identificadores de símbolo predefinidos](../windows/predefined-symbol-ids.md)<br/>