---
title: Usar conjuntos de reglas para especificar las reglas C++ que se van a ejecutar
ms.date: 04/28/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.native
ms.openlocfilehash: 5cf0f88c6937f4c1609a29fd618af0fdadad4437
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/17/2020
ms.locfileid: "79467124"
---
# <a name="use-rule-sets-to-specify-the-c-rules-to-run"></a>Usar conjuntos de reglas para especificar C++ las reglas que se van a ejecutar

En Visual Studio, puede crear y modificar un conjunto de *reglas* personalizado para satisfacer las necesidades específicas del proyecto asociadas con el análisis de código. Los conjuntos de reglas predeterminados se almacenan en `%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets`.

**Visual Studio 2017 versión 15,7 y versiones posteriores:** Puede crear conjuntos de reglas personalizadas mediante cualquier editor de texto y aplicarlos en compilaciones de línea de comandos, independientemente del sistema de compilación que esté usando. Para obtener más información, vea [/Analyze: ruleset](/cpp/build/reference/analyze-code-analysis).

Para crear un conjunto C++ de reglas personalizado en Visual Studio, un proyectoC++ de C/debe estar abierto en el IDE de Visual Studio. A continuación, se abre un conjunto de reglas estándar en el editor de conjuntos de reglas y, a continuación, se agregan o quitan reglas específicas y, opcionalmente, se cambia la acción que se produce cuando el análisis de código determina que se ha infringido una regla.

Para crear un nuevo conjunto de reglas personalizado, guárdelo con un nuevo nombre de archivo. El conjunto de reglas personalizado se asigna automáticamente al proyecto.

## <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Para crear una regla personalizada a partir de un solo conjunto de reglas existente

1. En el Explorador de soluciones, abra el menú contextual del proyecto y, a continuación, elija **propiedades**.

1. En la pestaña **propiedades** , elija **análisis de código**.

1. En la lista desplegable **conjunto de reglas** , realice una de las acciones siguientes:

   - Elija el conjunto de reglas que desea personalizar.

     \- O bien

   - Elija **\<examinar... >** para especificar un conjunto de reglas existente que no está en la lista.

1. Elija **abrir** para mostrar las reglas en el editor de conjuntos de reglas.

## <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Para modificar un conjunto de reglas en el editor de conjuntos de reglas

- Para cambiar el nombre para mostrar del conjunto de reglas, en el menú **Ver** , elija **ventana Propiedades**. Escriba el nombre para mostrar en el cuadro **nombre** . Observe que el nombre para mostrar puede diferir del nombre de archivo.

- Para agregar todas las reglas del grupo a un conjunto de reglas personalizado, active la casilla del grupo. Para quitar todas las reglas del grupo, desactive la casilla.

- Para agregar una regla concreta al conjunto de reglas personalizado, active la casilla de la regla. Para quitar la regla del conjunto de reglas, desactive la casilla.

- Para cambiar la acción realizada cuando se infringe una regla en un análisis de código, elija el campo **acción** de la regla y, a continuación, elija uno de los siguientes valores:

     **ADVERTENCIA** : genera una advertencia.

     **Error** : genera un error.

     **Info** : genera un mensaje.

     **Ninguno** : deshabilita la regla. Esta acción es igual que quitar la regla del conjunto de reglas.

## <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Para agrupar, filtrar o cambiar los campos del editor de conjuntos de reglas mediante la barra de herramientas del editor

- Para expandir las reglas de todos los grupos, seleccione **expandir todo**.

- Para contraer las reglas de todos los grupos, elija **contraer todo**.

- Para cambiar el campo por el que se agrupan las reglas, elija el campo en la lista **Agrupar por** . Para mostrar las reglas sin agrupar, elija **\<ninguno >** .

- Para agregar o quitar campos en columnas de regla, elija **Opciones de columna**.

- Para ocultar reglas que no se aplican a la solución actual, elija **Ocultar reglas que no se aplican a la solución actual**.

- Para cambiar entre mostrar y ocultar reglas que tienen asignada la acción error, elija **Mostrar reglas que pueden generar errores de análisis de código**.

- Para cambiar entre mostrar y ocultar reglas que tienen asignada la acción ADVERTENCIA, elija **Mostrar reglas que pueden generar advertencias de análisis de código**.

- Para cambiar entre mostrar y ocultar reglas que tienen asignada la acción **ninguno** , elija **Mostrar reglas que no estén habilitadas**.

- Para agregar o quitar conjuntos de reglas predeterminadas de Microsoft en el conjunto de reglas actual, elija **Agregar o quitar conjuntos de reglas secundarios**.

## <a name="to-create-a-rule-set-in-a-text-editor"></a>Para crear un conjunto de reglas en un editor de texto

Puede crear un conjunto de reglas personalizado en un editor de texto, almacenarlo en cualquier ubicación con una extensión de `.ruleset` y aplicar con la opción del compilador [/Analyze: ruleset](/cpp/build/reference/analyze-code-analysis) .

En el ejemplo siguiente se muestra un archivo de conjunto de reglas básico que puede usar como punto de partida:

::: moniker range="<=vs-2017"

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end

::: moniker range=">=vs-2019"

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end
