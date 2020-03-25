---
ms.openlocfilehash: e2b88bb1c60c97c9f63caacfb98ba87e0443e799
ms.sourcegitcommit: 44eeb065c3148d0484de791080a3f963109744fc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "79509444"
---
# <a name="contributing"></a>Contribución

Le agradecemos su interés en colaborar con la documentación de Visual C++.

En este tema, comprobará cuál es el proceso básico para agregar o actualizar el contenido del [sitio de documentación de Visual C++](https://docs.microsoft.com/cpp).

Abordaremos lo siguiente:

* [Proceso de contribución](#process-for-contributing)
* [Qué se debe hacer y qué no](#dos-and-donts)
* [Creación de los documentos](#building-the-docs)
* [Contribución a los ejemplos](#contributing-to-samples)
* [Contrato de licencia de colaboración](#contributor-license-agreement)

## <a name="process-for-contributing"></a>Proceso de contribución

**Paso 1:** abra un asunto en el que describa el artículo que quiere redactar y su relación con el contenido existente.
El contenido de la carpeta **docs** se organiza en secciones por área de contenido (por ejemplo, depurador). Determine en qué carpeta deberá incluirse el contenido nuevo. Recabe opiniones sobre su propuesta.

Si los cambios son pequeños, puede omitir este primer paso.

**Paso 2:** bifurque el repositorio `MicrosoftDocs/cpp-docs`.

**Paso 3:** cree una rama (`branch`) para el artículo.

**Paso 4:** redacte el artículo.

Si es un tema nuevo, puede usar esta [plantilla](./styleguide/template.md) como punto de partida. La plantilla contiene las instrucciones de escritura y la explicación de los metadatos necesarios para cada artículo, como la información del autor.

Vaya a la carpeta correspondiente a la ubicación de la tabla de contenido que se determinó para su artículo en el paso 1.
Esa carpeta contiene los archivos Markdown de todos los artículos incluidos en esa sección. Si es necesario, cree una carpeta para colocar los archivos de su contenido.

Agregue las imágenes y otros recursos estáticos a la subcarpeta denominada `media`. Si va a crear una carpeta nueva para el contenido, agregue una carpeta de elementos multimedia a la carpeta nueva.

Asegúrese de seguir la sintaxis de Markdown adecuada. Consulte la [guía de estilo](./styleguide/template.md) para obtener más información.

### <a name="example-structure"></a>Estructura de ejemplo

```
docs
    /standard-library
        wstring-convert-class.md
        /media
            wstring-conversion.png
```

**Paso 5:** Envíe una solicitud de incorporación de cambios (PR) desde su rama a `MicrosoftDocs/cpp-docs/master`.

Si la solicitud aborda un asunto existente, agregue la palabra clave `Fixes #Issue_Number` al mensaje de confirmación o a la descripción de la solicitud de incorporación de cambios. De este modo, el asunto se podrá cerrar automáticamente cuando se combine la solicitud. Para obtener más información, consulte [Closing issues via commit messages](https://help.github.com/articles/closing-issues-via-commit-messages/) (Cerrar asuntos mediante mensajes de confirmación).

El equipo de Visual Studio revisará su solicitud y le notificará si el cambio es correcto o si son necesarias otras modificaciones para aprobarlo.

**Paso 6:** Realice las actualizaciones necesarias a la rama que haya acordado con el equipo.

Los encargados del mantenimiento combinarán la solicitud con la rama principal una vez que se hayan aplicado los comentarios y el cambio no presente problemas.

Las confirmaciones de la rama principal se insertan en la rama en vivo siguiendo un ritmo determinado. Una vez insertadas, podrá ver su contribución en [docs.microsoft.com](https://docs.microsoft.com/cpp/).

## <a name="dos-and-donts"></a>Qué hacer y qué no hacer

En la lista siguiente se incluye una serie de reglas orientativas que se deben tener en cuenta a la hora de colaborar en la documentación de .NET.

- **NO** solicite la incorporación de grandes cambios. En su lugar, registre un asunto e inicie una discusión para que podamos definir un rumbo antes de dedicar una gran cantidad de tiempo.
- **LEA** la [guía de estilo](./styleguide/template.md) y las instrucciones de [voz y tono](./styleguide/voice-tone.md).
- **USE** el archivo de [plantilla](./styleguide/template.md) como punto de partida del trabajo.
- **CREE** una rama independiente en la bifurcación antes de trabajar en los artículos.
- **SIGA** el [flujo de trabajo de GitHub](https://guides.github.com/introduction/flow/).
- **HABLE** de sus contribuciones con frecuencia en blogs o Twitter (o cualquier otra red social).

> [!NOTE]
> Es posible que observe que algunos de los temas no siguen actualmente todas las instrucciones que se especifican aquí y en la [guía de estilo](./styleguide/template.md), pero estamos trabajando para dar coherencia a todo el sitio. Compruebe la lista de [asuntos abiertos](https://github.com/MicrosoftDocs/cpp-docs/issues?q=is%3Aissue+is%3Aopen+label%3Aguidelines-adherence) de los que estamos realizando un seguimiento con vistas a ese objetivo.

## <a name="building-the-docs"></a>Creación de los documentos

La documentación se escribe en [GitHub Flavored Markdown](https://help.github.com/categories/writing-on-github/) y se crea mediante [DocFX](https://dotnet.github.io/docfx/) y otras herramientas internas de publicación o creación. Se hospeda en [docs.microsoft.com](https://docs.microsoft.com/).

Si desea crear los documentos de forma local, deberá instalar [DocFX](https://dotnet.github.io/docfx/); se recomienda usar las versiones más recientes.

Hay varias formas de utilizar DocFX, y la mayoría de ellas se abordan en la [guía de introducción de DocFX](https://dotnet.github.io/docfx/tutorial/docfx_getting_started.html). Las instrucciones siguientes usan la versión [basada en la línea de comandos](https://dotnet.github.io/docfx/tutorial/docfx_getting_started.html#2-use-docfx-as-a-command-line-tool) de la herramienta. Si está familiarizado con otras formas enumeradas en el vínculo anterior, puede usarlas.

**Nota:** Actualmente, DocFX requiere .NET Framework en Windows o Mono (para Linux o macOS). Nuestra intención es portarlo a .NET Core en el futuro.

Con un servidor web integrado, puede crear y obtener una vista previa local del sitio resultante. Vaya a la carpeta `cpp-docs\docs` de su equipo y escriba el comando siguiente:

> docfx -t default --serve

Esto inicia la vista previa local en [localhost:8080](http://localhost:8080). A continuación, para ver los cambios, vaya a `http://localhost:8080/[path]`, por ejemplo `http://localhost:8080/cpp/visual-cpp-in-visual-studio.html`.

**Nota:** Actualmente, la vista previa local no contiene temas, por lo que la apariencia y el comportamiento no serán los mismos que en el sitio de documentación. Estamos trabajando para mejorar esta experiencia. También utilizamos algunas extensiones personalizadas para los vídeos y notas insertados, y los documentos incluidos, que no se podrán ver en la versión preliminar.

## <a name="contributing-to-samples"></a>Contribución a los ejemplos

Por ahora, incluya en el artículo el código de ejemplo requerido como bloques de código alineado. El repositorio tiene una carpeta `codesnippets`, pero no es posible realizar contribuciones públicas.

## <a name="contributor-license-agreement"></a>Contrato de licencia de colaboración

Debe firmar el [Contrato de licencia de colaboración (CLA)](LICENSE) para que se combine su PR. Es un requisito único para los proyectos de docs.microsoft.com. Puede obtener más información sobre los [contratos de licencia de colaboración (CLA)](https://en.wikipedia.org/wiki/Contributor_License_Agreement) en Wikipedia.

No tiene que firmar el contrato con antelación. Puede clonar, bifurcar y enviar la PR de la forma habitual. Cuando se haya creado la PR, un bot de CLA se encargará de clasificarla. Si el cambio no es relevante (por ejemplo, si ha corregido un error ortográfico), la PR se etiqueta como "CLA-not-required" (el CLA no es obligatorio). En caso contrario, se etiqueta como "CLA-required" (el CLA es obligatorio). Una vez que haya firmado el CLA, la solicitud de incorporación de cambios actual y las próximas se etiquetarán como "CLA-signed" (se ha firmado el CLA).
