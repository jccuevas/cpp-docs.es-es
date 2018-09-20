---
title: 'TN057: Localización de componentes de MFC | Microsoft Docs'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.components
dev_langs:
- C++
helpviewer_keywords:
- components [MFC], localizing
- TN057
- resources [MFC], localization
- localization [MFC], MFC resources
- localization [MFC], MFC components
- MFC DLLs [MFC], localizing
- DLLs [MFC], localizing MFC
- localization [MFC], resources
ms.assetid: 5376d329-bd45-41bd-97f5-3d895a9a0af5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8dcd3117d50d2d8905e5382cf226ba487c13a7c7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414217"
---
# <a name="tn057-localization-of-mfc-components"></a>TN057: Localización de componentes de MFC

> [!NOTE]
> La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea. Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos. Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.

Esta nota describe algunos de los diseños y procedimientos que puede usar para localizar el componente, si se controla una aplicación o una OLE o un archivo DLL que utiliza MFC.

## <a name="overview"></a>Información general

En realidad hay dos problemas para resolver cuándo adaptar un componente que utiliza MFC. En primer lugar, debe localizar sus propios recursos, cadenas, los cuadros de diálogo y otros recursos que son específicas de su componente. Mayoría de los componentes creada con MFC también incluye y usa un número de recursos definidos por MFC. Debe proporcionar también los recursos MFC localizados. Afortunadamente, MFC ya proporciona varios lenguajes.

Además, el componente debe estar preparado para ejecutarse en su entorno de destino (entorno de Europa o habilitados para DBCS). En su mayor parte, esto depende de la aplicación tratar correctamente los caracteres con el conjunto de bits altos y manipulación de cadenas de caracteres de doble byte. MFC está habilitada, de forma predeterminada, tanto de estos entornos, para que sea posible tener un solo archivo binario en todo el mundo que se usa en todas las plataformas con solo distintos recursos conectados durante la instalación.

## <a name="localizing-your-components-resources"></a>Localización de recursos de componentes

Localizar la aplicación o el archivo DLL debe implicar bastaría con reemplazar los recursos con los recursos que coinciden con el lenguaje de destino. Para sus propios recursos, esto es relativamente sencillo: modificar los recursos en el editor de recursos y compilar la aplicación. Si el código está escrito correctamente no habrá cadenas o texto que desea localizar codificado de forma rígida en el código fuente de C++ - localización todos puede realizarse simplemente hay que modificar los recursos. De hecho, puede implementar el componente de forma que todos los que proporciona una versión localizada implican incluso una compilación del código original. Esto es más complejo, pero merece la pena y es el mecanismo elegido para MFC. También es posible localizar una aplicación, cargar el archivo EXE o DLL en el editor de recursos y modificar directamente los recursos. Si bien es posible, requiere volver a aplicar esos cambios cada vez que compile una nueva versión de la aplicación.

Una forma de evitar consiste en ubicar todos los recursos en un archivo DLL independiente, denominada a veces un archivo DLL satélite. Este archivo DLL, a continuación, se carga dinámicamente en tiempo de ejecución y los recursos se cargan desde ese archivo DLL en lugar de desde el módulo principal con todo el código. MFC admite directamente este enfoque. Considere la posibilidad de una aplicación denominada MYAPP. EXE; Esto podría tener todos sus recursos en un archivo DLL denominado MYRES. ARCHIVO DLL. En la aplicación `InitInstance` realizaría lo siguiente para cargar ese DLL y hacer que MFC cargar recursos desde esa ubicación:

```cpp
CMyApp::InitInstance()
{
    // one of the first things in the init code
    HINSTANCE hInst = LoadLibrary("myres.dll");

    if (hInst != NULL)
        AfxSetResourceHandle(hInst);

    // other initialization code would follow
    // ...
}
```

Desde ese momento, MFC cargará los recursos de ese archivo DLL en lugar de desde myapp.exe. Todos los recursos, sin embargo, deben estar presentes en ese archivo DLL; MFC no buscará en la instancia de la aplicación en busca de un recurso determinado. Esta técnica aplica igualmente bien a regular archivos DLL de MFC así como controles OLE. El programa de instalación se copiaría la versión adecuada de MYRES. Dependiendo de qué configuración regional de recursos DLL en la que desea que el usuario.

Es relativamente fácil crear un recurso solo archivo DLL. Crear un proyecto DLL, agregue su. RC a él y agréguele los recursos necesarios. Si tiene un proyecto existente que no utiliza esta técnica, puede copiar los recursos de ese proyecto. Después de agregar el archivo de recursos al proyecto, está casi listo para compilar el proyecto. Lo único que debe hacer es establecer las opciones para incluir el vinculador **/NOENTRY**. Esto indica al vinculador que el archivo DLL no tiene ningún punto de entrada - dado que no tiene ningún código, no tiene ningún punto de entrada.

> [!NOTE]
> El editor de recursos en Visual C++ 4.0 y versiones posteriores admite varios idiomas por. Archivo RC. Esto puede hacer muy fácil de administrar la localización en un solo proyecto. Los recursos para cada idioma se controlan mediante las directivas de preprocesador generadas por el editor de recursos.

## <a name="using-the-provided-mfc-localized-resources"></a>Mediante el MFC proporcionado de recursos localizados

Cualquier aplicación MFC que compile vuelve a utilizar dos cosas de MFC: código y los recursos. Es decir, MFC tiene diversos mensajes de error, cuadros de diálogo integrados y otros recursos que se usan las clases de MFC. Para localizar completamente la aplicación, tiene que localizar recursos de su aplicación pero los recursos que proceden directamente de MFC. MFC proporciona a una serie de lenguaje diferentes archivos de recursos automáticamente, por lo que si el idioma de destino es uno de los lenguajes MFC ya es compatible con, solo deberá asegurarse de que use esos recursos localizados.

Cuando se redactó este documento, MFC admite chino, alemán, español, francés, italiano, japonés y coreano. Los archivos que contienen estas versiones localizadas están en el MFC\INCLUDE\L.* (la "L" significa para localizados) directorios. Los archivos de alemán son en MFC\INCLUDE\L.DEU, por ejemplo. Para hacer que la aplicación para usar estos archivos RC en lugar de los archivos ubicados en MFC\INCLUDE, agregue un `/IC:\PROGRAM FILES\MICROSOFT VISUAL STUDIO .NET 2003\VC7\MFC\INCLUDE\L.DEU` a la línea de comandos de RC (Esto es solo un ejemplo; debe sustituir la configuración regional de elección, así como el directorio en el que instaló Visual C ++).

Las instrucciones anteriores funcionará si la aplicación está vinculado estáticamente a MFC. La mayoría de las aplicaciones vinculan dinámicamente (ya que es el valor predeterminado de AppWizard). En este escenario, no solo el código es dinámicamente vinculado - ¿son los recursos. Como resultado, puede localizar los recursos en la aplicación, pero los recursos de implementación de MFC se cargará desde el MFC7x.DLL (o una versión posterior) o desde MFC7xLOC.DLL si existe. Se puede enfocar desde distintos dos ángulos.

El enfoque más complejo consiste en enviar uno de los MFC7xLOC.DLLs localizada (por ejemplo, MFC7xDEU para alemán, MFC7xESP.DLL para español, etc.) o una versión posterior e instale el MFC7xLOC.DLL adecuado en el directorio del sistema cuando el usuario instala la aplicación. Esto puede ser muy compleja para el desarrollador y el usuario final y por lo tanto no se recomienda. Consulte [56 de nota técnica](../mfc/tn056-installation-of-localized-mfc-components.md) para obtener más información sobre esta técnica y sus advertencias.

El enfoque más sencillo y más seguro consiste en incluir los recursos MFC localizados en su aplicación o DLL propio (o su DLL satélite si está usando uno). Esto evita los problemas de instalación MFC7xLOC.DLL correctamente. Para ello, siga las mismas instrucciones para el caso estática proporcionada más arriba (establecimiento de la línea de comandos de RC correctamente para que apunte a los recursos localizados), excepto que también debe quitar la `/D_AFXDLL` define y que se ha agregado por el Asistente para aplicaciones. Cuando `/D_AFXDLL` está definido, AFXRES. H (y los demás archivos RC de MFC) define todos los recursos (debido a se van a extraer de los archivos DLL de MFC en su lugar).

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)
