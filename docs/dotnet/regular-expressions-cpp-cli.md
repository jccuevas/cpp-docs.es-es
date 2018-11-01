---
title: Eexpresiones regulares (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- regular expressions [C++]
- .NET Framework [C++], regular expressions
- regular expressions [C++], about regular expressions
- parsing strings [C++]
- examples [C++], strings
- regular expressions [C++], parsing strings
- Split method, parsing strings
- strings [C++], parsing
- substrings, simple matches
- searching, exact substring matches
- strings [C++], exact substring matching
- regular expressions [C++], simple matching
- IsMatch method
- strings [C++], extracting data from
- formatted strings [C++]
- regular expressions [C++], extracting data fields
- data [C++], extracting from strings
- regular expressions [C++], rearranging data
- data [C++], rearranging
- search and replace
- Replace method
- regular expressions [C++], search and replace
- strings [C++], formatting
- data [C++], formatting
- regular expressions [C++], validating data formatting
ms.assetid: 838bab49-0dbc-4089-a604-ef146269ef5a
ms.openlocfilehash: ace05ffc0c9b0357e40f7a2520921c672014b9ff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604339"
---
# <a name="regular-expressions-ccli"></a>Eexpresiones regulares (C++/CLI)

Muestra distintas operaciones de cadena mediante las clases de expresiones regulares en .NET Framework.

Los temas siguientes muestran el uso de .NET Framework <xref:System.Text.RegularExpressions> espacio de nombres (y en un caso la <xref:System.String.Split%2A?displayProperty=fullName> método) para buscar, analizar y modificar las cadenas.

## <a name="parse_regex"></a> Analizar cadenas mediante expresiones regulares

En el siguiente ejemplo de código se muestra el análisis de una cadena sencilla mediante la clase <xref:System.Text.RegularExpressions.Regex> del espacio de nombres <xref:System.Text.RegularExpressions?displayProperty=fullName>. Se crea una cadena que contiene varios tipos de descriptores de palabras. A continuación, se analiza la cadena mediante las clases <xref:System.Text.RegularExpressions.Regex> y <xref:System.Text.RegularExpressions.Match>. Finalmente, se muestran todas las palabras de la frase independientemente.

### <a name="example"></a>Ejemplo

```cpp
// regex_parse.cpp
// compile with: /clr
#using <system.dll>

using namespace System;
using namespace System::Text::RegularExpressions;

int main( )
{
   int words = 0;
   String^ pattern = "[a-zA-Z]*";
   Console::WriteLine( "pattern : '{0}'", pattern );
   Regex^ regex = gcnew Regex( pattern );

   String^ line = "one\ttwo three:four,five six  seven";
   Console::WriteLine( "text : '{0}'", line );
   for( Match^ match = regex->Match( line );
        match->Success; match = match->NextMatch( ) )
   {
      if( match->Value->Length > 0 )
      {
         words++;
         Console::WriteLine( "{0}", match->Value );
      }
   }
   Console::WriteLine( "Number of Words : {0}", words );

   return 0;
}
```

## <a name="parse_split"></a> Analizar cadenas mediante el método Split

En el ejemplo de código siguiente se muestra cómo utilizar el método <xref:System.String.Split%2A?displayProperty=fullName> para extraer todas las palabras de una cadena. Se construye una cadena que contiene varios tipos de perfiladores de palabras y, a continuación, se analiza llamando a <xref:System.String.Split%2A> con una lista de los perfiladores. Finalmente, se muestran todas las palabras de la frase independientemente.

### <a name="example"></a>Ejemplo

```cpp
// regex_split.cpp
// compile with: /clr
using namespace System;

int main()
{
   String^ delimStr = " ,.:\t";
   Console::WriteLine( "delimiter : '{0}'", delimStr );
   array<Char>^ delimiter = delimStr->ToCharArray( );
   array<String^>^ words;
   String^ line = "one\ttwo three:four,five six seven";

   Console::WriteLine( "text : '{0}'", line );
   words = line->Split( delimiter );
   Console::WriteLine( "Number of Words : {0}", words->Length );
   for (int word=0; word<words->Length; word++)
      Console::WriteLine( "{0}", words[word] );

   return 0;
}
```

## <a name="regex_simple"></a> Usar expresiones regulares para buscar coincidencias simples

El ejemplo de código siguiente usa expresiones regulares para buscar coincidencias exactas de subcadenas. La búsqueda se realiza por estático <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> método, que toma dos cadenas como entrada. La primera es la cadena se va a buscar y el segundo es el patrón que se va a buscar.

### <a name="example"></a>Ejemplo

```cpp
// regex_simple.cpp
// compile with: /clr
#using <System.dll>

using namespace System;
using namespace System::Text::RegularExpressions;

int main()
{
   array<String^>^ sentence =
   {
      "cow over the moon",
      "Betsy the Cow",
      "cowering in the corner",
      "no match here"
   };

   String^ matchStr = "cow";
   for (int i=0; i<sentence->Length; i++)
   {
      Console::Write( "{0,24}", sentence[i] );
      if ( Regex::IsMatch( sentence[i], matchStr,
                     RegexOptions::IgnoreCase ) )
         Console::WriteLine("  (match for '{0}' found)", matchStr);
      else
         Console::WriteLine("");
   }
   return 0;
}
```

## <a name="regex_extract"></a> Usar expresiones regulares para extraer campos de datos

En el ejemplo de código siguiente se muestra el uso de expresiones regulares para extraer datos de una cadena con formato. El siguiente ejemplo de código utiliza el <xref:System.Text.RegularExpressions.Regex> clase para especificar un patrón que corresponde a una dirección de correo electrónico. Este modelo incluye los identificadores de campo que pueden usarse para recuperar el usuario y las partes del nombre de host de cada dirección de correo electrónico. La <xref:System.Text.RegularExpressions.Match> clase se usa para realizar la coincidencia de modelos. Si la dirección de correo electrónico determinado es válida, se extraen y se muestran el nombre de usuario y nombres de host.

### <a name="example"></a>Ejemplo

```cpp
// Regex_extract.cpp
// compile with: /clr
#using <System.dll>

using namespace System;
using namespace System::Text::RegularExpressions;

int main()
{
    array<String^>^ address=
    {
        "jay@southridgevideo.com",
        "barry@adatum.com",
        "treyresearch.net",
        "karen@proseware.com"
    };

    Regex^ emailregex = gcnew Regex("(?<user>[^@]+)@(?<host>.+)");

    for (int i=0; i<address->Length; i++)
    {
        Match^ m = emailregex->Match( address[i] );
        Console::Write("\n{0,25}", address[i]);

        if ( m->Success )
        {
            Console::Write("   User='{0}'",
            m->Groups["user"]->Value);
            Console::Write("   Host='{0}'",
            m->Groups["host"]->Value);
        }
        else
            Console::Write("   (invalid email address)");
        }

    Console::WriteLine("");
    return 0;
}
```

## <a name="regex_rearrange"></a> Usar expresiones regulares para reorganizar los datos

En el ejemplo de código siguiente se muestra cómo se puede usar la compatibilidad con expresiones regulares de .NET Framework para reorganizar o volver a formatear datos. El siguiente ejemplo de código utiliza el <xref:System.Text.RegularExpressions.Regex> y <xref:System.Text.RegularExpressions.Match> clases para extraer nombres y apellidos de una cadena y, a continuación, mostrar estos elementos en orden inverso.

La <xref:System.Text.RegularExpressions.Regex> clase se utiliza para construir una expresión regular que describe el formato actual de los datos. Los dos nombres se supone que estar separados por una coma y pueden usar cualquier cantidad de espacio en blanco alrededor de la coma. El <xref:System.Text.RegularExpressions.Match> método, a continuación, se usa para analizar cada cadena. Si se realiza correctamente, se recuperan los nombres y apellidos de los <xref:System.Text.RegularExpressions.Match> de objeto y se muestra.

### <a name="example"></a>Ejemplo

```cpp
// regex_reorder.cpp
// compile with: /clr
#using <System.dll>
using namespace System;
using namespace Text::RegularExpressions;

int main()
{
   array<String^>^ name =
   {
      "Abolrous, Sam",
      "Berg,Matt",
      "Berry , Jo",
      "www.contoso.com"
   };

   Regex^ reg = gcnew Regex("(?<last>\\w*)\\s*,\\s*(?<first>\\w*)");

   for ( int i=0; i < name->Length; i++ )
   {
      Console::Write( "{0,-20}", name[i] );
      Match^ m = reg->Match( name[i] );
      if ( m->Success )
      {
         String^ first = m->Groups["first"]->Value;
         String^ last = m->Groups["last"]->Value;
         Console::WriteLine("{0} {1}", first, last);
      }
      else
         Console::WriteLine("(invalid)");
   }
   return 0;
}
```

## <a name="regex_search"></a> Usar expresiones regulares para buscar y reemplazar

En el ejemplo de código siguiente se muestra cómo la clase de expresión regular <xref:System.Text.RegularExpressions.Regex> puede usarse para realizar la búsqueda y reemplazo. Esto se realiza con el <xref:System.Text.RegularExpressions.Regex.Replace%2A> método. La versión utilizada toma dos cadenas como entrada: la cadena que se va a modificar y la cadena que se va a insertar en lugar de las secciones (si existe) que coinciden con el modelo dado el <xref:System.Text.RegularExpressions.Regex> objeto.

Este código reemplaza todos los dígitos de una cadena con caracteres de subrayado (_) y, a continuación, reemplaza aquellos con una cadena vacía, con lo que quitaría ellos. Se puede lograr el mismo efecto en un solo paso, pero dos pasos se usan aquí para fines de demostración.

### <a name="example"></a>Ejemplo

```cpp
// regex_replace.cpp
// compile with: /clr
#using <System.dll>
using namespace System::Text::RegularExpressions;
using namespace System;

int main()
{
   String^ before = "The q43uick bro254wn f0ox ju4mped";
   Console::WriteLine("original  : {0}", before);

   Regex^ digitRegex = gcnew Regex("(?<digit>[0-9])");
   String^ after = digitRegex->Replace(before, "_");
   Console::WriteLine("1st regex : {0}", after);

   Regex^ underbarRegex = gcnew Regex("_");
   String^ after2 = underbarRegex->Replace(after, "");
   Console::WriteLine("2nd regex : {0}", after2);

   return 0;
}
```

## <a name="regex_validate"></a> Usar expresiones regulares para validar el formato de datos

En el ejemplo de código siguiente se muestra el uso de expresiones regulares para comprobar el formato de una cadena. En el ejemplo de código siguiente, la cadena debe contener un número de teléfono válido. En el ejemplo de código siguiente se usa la cadena "\d{3}-\d{3}-\d{4}" para indicar que cada campo representa un número de teléfono válido. "D" en la cadena indica un dígito y el argumento después de cada "d" indica el número de dígitos que deben estar presentes. En este caso, el número se debe estar separado por guiones.

### <a name="example"></a>Ejemplo

```cpp
// regex_validate.cpp
// compile with: /clr
#using <System.dll>

using namespace System;
using namespace Text::RegularExpressions;

int main()
{
   array<String^>^ number =
   {
      "123-456-7890",
      "444-234-22450",
      "690-203-6578",
      "146-893-232",
      "146-839-2322",
      "4007-295-1111",
      "407-295-1111",
      "407-2-5555",
   };

   String^ regStr = "^\\d{3}-\\d{3}-\\d{4}$";

   for ( int i = 0; i < number->Length; i++ )
   {
      Console::Write( "{0,14}", number[i] );

      if ( Regex::IsMatch( number[i], regStr ) )
         Console::WriteLine(" - valid");
      else
         Console::WriteLine(" - invalid");
   }
   return 0;
}
```

## <a name="related-sections"></a>Secciones relacionadas

[Expresiones regulares de .NET Framework](/dotnet/standard/base-types/regular-expressions)

## <a name="see-also"></a>Vea también

[Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)