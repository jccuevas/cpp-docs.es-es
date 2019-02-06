---
title: Cambiar un símbolo
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.changing
- vc.editors.symbol.restrictions.name
- vc.editors.symbol.changing.value
- vc.editors.symbol.restrictions.value
- vc.editors.symbol.changing.header
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
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
ms.openlocfilehash: 7d2890c2d2c05f1ee0309446dfe2de9917f85707
ms.sourcegitcommit: 63c072f5e941989636f5a2b13800b68bb7129931
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/06/2019
ms.locfileid: "55763991"
---
# <a name="changing-a-symbol"></a>Cambiar un símbolo

Cuando se crea un nuevo recurso u objeto de recurso, el entorno de desarrollo le asigna un nombre de símbolo predeterminado, por ejemplo, IDD_DIALOG1. Puede usar el [ventana propiedades](/visualstudio/ide/reference/properties-window) para cambiar el nombre del símbolo predeterminado o para cambiar el nombre de cualquier símbolo ya asociado a un recurso.

Para los símbolos asociados a un único recurso, también puede usar el **propiedades** ventana para cambiar el valor de símbolo. Puede usar el [cuadro de diálogo símbolos de recursos](../windows/resource-symbols-dialog-box.md) para cambiar el valor de los símbolos no estén asignados a un recurso. Para obtener más información, consulte [cambiar símbolos sin asignar](../windows/changing-unassigned-symbols.md).

Normalmente todos los símbolos se guardan las definiciones en `Resource.h`. Sin embargo, puede que necesite cambiar este nombre de archivo de inclusión para, por ejemplo, poder trabajar con más de un archivo de recursos en el mismo directorio.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*.

## <a name="to-change-a-resources-symbol-name-id"></a>Para cambiar el nombre de un recurso de símbolo (Id.)

1. En [vista de recursos](../windows/resource-view-window.md), seleccione el recurso.

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

1. En el **propiedades** ventana, escriba un nombre de símbolo nuevo o seleccione en la lista de símbolos existentes en el **ID** cuadro.

   Si escribe un nombre de símbolo nuevo, se le asigna automáticamente un valor.

Puede usar el [cuadro de diálogo símbolos de recursos](../windows/resource-symbols-dialog-box.md) para cambiar los nombres de los símbolos no estén asignados a un recurso. Para obtener más información, consulte [cambiar símbolos sin asignar](../windows/changing-unassigned-symbols.md).

### <a name="symbol-name-restrictions"></a>Restricciones de nombre de símbolo

Las restricciones en los nombres de símbolos son las siguientes:

- Todos los [símbolos](../windows/symbols-resource-identifiers.md) debe ser único dentro del ámbito de la aplicación. Esto evita conflictos de definiciones de símbolos en los archivos de encabezado.

- Los caracteres válidos en un nombre de símbolo son A-z, a-z, 0-9 y caracteres de subrayado (_).

- Los nombres de símbolo no pueden empezar por un número y se limitan a 247 caracteres.

- Los nombres de símbolo no pueden contener espacios.

- Los nombres de símbolo no distinguen entre mayúsculas y minúsculas, pero se conservan las mayúsculas o minúsculas de la primera definición de símbolos. El compilador/editor de recursos y los programas de C++  usan el archivo de encabezado que define los símbolos para hacer referencia a los recursos definidos en un archivo de recursos. Cuando dos nombres de símbolo difieren únicamente en sus mayúsculas o minúsculas, el programa de C++ verá dos símbolos distintos, mientras que el compilador/editor de recursos verá dos nombres se remiten al mismo símbolo.

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

## <a name="to-change-a-symbol-value-assigned-to-a-single-resource-or-object"></a>Para cambiar el valor de un símbolo asignado a un solo recurso u objeto

1. En [vista de recursos](../windows/resource-view-window.md), seleccione el recurso.

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

1. En el **propiedades** ventana, escriba el nombre del símbolo seguido por un signo igual y un número entero en el **ID** cuadro, por ejemplo:

    ```
    IDC_EDITNAME=5100
    ```

El nuevo valor se almacena en el archivo de encabezado de símbolos la próxima vez que guarde el proyecto. En el cuadro Id. solo está visible el nombre del símbolo; el signo igual y el valor no se muestran después de su validación.

### <a name="symbol-value-restrictions"></a>Restricciones de valor de símbolo

Un valor de símbolo puede ser cualquier entero expresado de la forma normal para las directivas de preprocesador #define. A continuación se muestran algunos ejemplos de valores de símbolo:

```
18
4001
0x0012
-3456
```

Los valores de símbolo de recursos (aceleradores, mapas de bits, cursores, cuadros de diálogo, iconos, menús, tablas de cadenas e información de versión) deben ser números decimales comprendidos en el intervalo de 0 a 32.767 (pero no pueden ser hexadecimales). Los valores de símbolo de partes de recursos, como los controles de cuadro de diálogo o las cadenas individuales de la tabla de cadenas, pueden ir de 0 a 65.534 o de -32.768 a 32.767.

Los símbolos de recursos son números de 16 bits. Puede especificarlos con o sin signo, pero se usan internamente como enteros sin signo. Así pues, los números negativos se convertirán a su valor positivo correspondiente.

A continuación se muestran algunas limitaciones de los valores de símbolo:

- El entorno de desarrollo de Visual Studio y MFC usan algunos intervalos numéricos para fines especiales. MFC se reserva todos los números con el bit más significativo establecido (de -32.768 a -1 o de 32.768 a 65.534, en función del signo).

- No se puede definir un valor de símbolo usando otras cadenas de símbolo. Por ejemplo, no se admite la siguiente definición de símbolo:

    ```cpp
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported
    ```

- No se puede usar macros de preprocesador con argumentos como definiciones de valor. Por ejemplo:

    ```cpp
    #define   IDD_ABOUT  ID(7) //not supported
    ```

   no es una expresión válida, independientemente de cómo se evalúe `ID` en tiempo de compilación.

- La aplicación puede tener un archivo que contenga símbolos definidos con expresiones. Para obtener más información sobre cómo incluir los símbolos como símbolos de solo lectura, consulte [símbolos utilizando compartidos (de solo lectura) o calculados](../windows/including-shared-read-only-or-calculated-symbols.md).

Para obtener más información sobre los intervalos numéricos, vea [TN023: Recursos de MFC estándar](../mfc/tn023-standard-mfc-resources.md).

## <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>Para cambiar el nombre del archivo de encabezado de símbolos de recurso

1. En [vista de recursos](../windows/resource-view-window.md), haga clic en el archivo .rc y elija [incluye recursos](../windows/resource-includes-dialog-box.md) en el menú contextual.

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

1. En el **archivo de encabezado de símbolos** , escriba el nuevo nombre del archivo de inclusión.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Identificadores de símbolo predefinidos](../windows/predefined-symbol-ids.md)<br/>
[Visualización de símbolos de recursos](../windows/viewing-resource-symbols.md)<br/>
