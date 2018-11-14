---
title: 'TN020: Convenciones de nomenclatura y numeración de identificadores'
ms.date: 11/04/2016
f1_keywords:
- vc.id
helpviewer_keywords:
- TN020
- resource identifiers, naming and numbering
- resource identifiers
ms.assetid: aecbd2cf-68b3-47f6-ae21-b1f507917245
ms.openlocfilehash: 9e575ee99b78b8efa75096cac4559eb9aea7fd21
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518676"
---
# <a name="tn020-id-naming-and-numbering-conventions"></a>TN020: Convenciones de nomenclatura y numeración de identificadores

En esta nota se describen las convenciones de nomenclatura y numeración de identificadores que MFC 2.0 utiliza para los recursos, los comandos, las cadenas, los controles y las ventanas secundarias.

Las convenciones de nomenclatura y numeración de identificadores de MFC se han diseñado para cumplir los requisitos siguientes:

- Proporcionar un estándar de nomenclatura de identificadores coherente en la biblioteca MFC y las aplicaciones MFC compatibles con el editor de recursos de Visual C++. Esto permite al programador interpretar el tipo y el origen de un recurso por su identificador.

- Enfatizar la relación 1 a 1 segura entre ciertos tipos de identificadores.

- Proporcionar conformidad con estándares ampliamente utilizado para asignar nombres a los identificadores en Windows.

- Dividir el espacio de numeración de los identificadores. El programador, MFC, Windows y los recursos editados con Visual C++ pueden asignar números de identificador. La creación de particiones adecuada ayudará a evitar la duplicación de números de identificador.

## <a name="the-id-prefix-naming-convention"></a>Convención de nomenclatura de prefijos de identificador

En una aplicación pueden aparecer varios tipos de identificadores. La convención de nomenclatura de identificadores de MFC define distintos prefijos para los diferentes tipos de recursos.

MFC utiliza el prefijo "IDR_" para indicar un id. de recurso que se aplica a varios tipos de recursos. Por ejemplo, para una ventana marco determinada, MFC utiliza el mismo prefijo “IDR_” para indicar un menú, un acelerador, una cadena y un recurso de icono. En la tabla siguiente se muestran los diferentes prefijos y su uso:

|Prefijo|Usar|
|------------|---------|
|IDR_|Para varios tipos de recursos (se utiliza principalmente para los menús, los aceleradores y las cintas).|
|IDD_|Para los recursos de plantilla de cuadro de diálogo (por ejemplo, IDD_DIALOG1).|
|IDC_|Para los recursos de cursor.|
|IDI_|Para los recursos de icono.|
|IDB_|Para los recursos de mapa de bits.|
|IDS_|Para los recursos de cadena.|

Dentro de un recurso DIALOG, MFC sigue estas convenciones:

|Prefijo o etiqueta|Usar|
|---------------------|---------|
|IDOK, IDCANCEL|Para los identificadores estándar de botón de comando.|
|IDC_|Para otros controles del cuadro de diálogo.|

El prefijo "IDC_" también se utiliza para los cursores. Este conflicto de denominación no suele ser un problema porque una aplicación típica tendrá pocos cursores y muchos controles de cuadro de diálogo.

Dentro de un recurso de menú, MFC sigue estas convenciones:

|Prefijo|Usar|
|------------|---------|
|IDM_|Para los elementos de menú que no utilizan la arquitectura de comandos de MFC.|
|ID_|Para los comandos de menú que utilizan la arquitectura de comandos de MFC.|

Los comandos que siguen la arquitectura de comandos MFC deben tener un controlador de comandos ON_COMMAND y pueden tener un controlador ON_UPDATE_COMMAND_UI. Si estos controladores de comandos siguen la arquitectura de comandos de MFC, funcionarán correctamente si se enlazan a un comando de menú, un botón de la barra de herramientas o un botón de la barra de cuadro de diálogo. El mismo prefijo "ID_" se utiliza también para una cadena de mensaje de menú que se muestra en la barra de mensajes del programa. La mayoría de los elementos de menú de la aplicación deben seguir las convenciones de comandos de MFC. Todos los identificadores de comando estándar (por ejemplo, ID_FILE_NEW) siguen esta convención.

MFC también utiliza "IDP_" como formato de cadenas especializado (en lugar de "IDS_"). Las cadenas con el prefijo "IDP_" son mensajes, es decir, cadenas utilizadas en cuadros de mensaje. Las cadenas "IDP_" pueden contener "%1" y "%2"como marcadores de posición de cadenas determinadas por el programa. Además suelen tener temas de Ayuda asociados, mientras que las cadenas "IDS_" no los tienen. Las cadenas "IDP_" siempre se traducen y las cadenas "IDS_" pueden no estar traducidas.

La biblioteca MFC también utiliza el prefijo "IDW_" como una forma especializada de identificadores de controles (en lugar de "IDC_"). Las clases del marco asignan estos identificadores a las ventanas secundarias, por ejemplo, las vistas y los divisores. Los id. de implementación de MFC llevan el prefijo "AFX_".

## <a name="the-id-numbering-convention"></a>Convención de numeración de identificadores

En la tabla siguiente se enumeran los intervalos válidos para los identificadores de los tipos específicos. Algunos de los límites se deben a la implementación técnica y otros son convenciones que se han diseñado para evitar que los identificadores entren en conflicto con los identificadores predefinidos de Windows o con las implementaciones predeterminadas de MFC.

Se recomienda encarecidamente definir todos los identificadores dentro de los intervalos recomendados. El límite inferior de estos intervalos es 1 porque 0 no se utiliza. Se recomienda utilizar la convención común y usar 100 o 101 como primer identificador.

|Prefijo|Tipo de recurso|Intervalo válido|
|------------|-------------------|-----------------|
|IDR_|varias|De 1 a 0x6FFF|
|IDD_|plantillas de cuadro de diálogo|De 1 a 0x6FFF|
|IDC_, IDI_, IDB_|cursores, iconos, mapas de bits|De 1 a 0x6FFF|
|IDS_, IDP_|cadenas generales|De 1 a 0x7FFF|
|ID_|comandos|De 0x8000 a 0xDFFF|
|IDC_|controles|De 8 a 0xDFFF|

Los motivos de estos límites de intervalo son las siguientes:

- Por convención, el valor de identificador de 0 no se utiliza.

- Las limitaciones de implementación de Windows exigen que los id. de recurso verdaderos sean menores o iguales que 0x7FFF.

- El marco interno de MFC se reserva estos intervalos:

  - De 0x7000 a 0x7FFF (vea afxres.h)

  - De 0xE000 a 0xEFFF (vea afxres.h)

  - De 16000 a 18000 (vea afxribbonres.h)

  Estos intervalos pueden cambiar en futuras implementaciones de MFC.

- Varios comandos del sistema de Windows utilizan el intervalo de 0xF000 a 0xFFFF.

- Los id. de control de 1 a 7 están reservados para controles estándar como IDOK e IDCANCEL.

- El intervalo de 0x8000 a 0xFFFF para las cadenas se reserva para los mensajes de menú de los comandos.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

