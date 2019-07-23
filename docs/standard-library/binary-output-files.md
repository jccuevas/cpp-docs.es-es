---
title: Archivos de salida binarios
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [C++], binary output files
- files [C++], binary output files
- binary data, binary output files
ms.assetid: 180954af-8cd6-444b-9a76-2f630a3389d8
ms.openlocfilehash: 4562f5c1167aeadc6689313e73545ed1ad9bbcf8
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376331"
---
# <a name="binary-output-files"></a>Archivos de salida binarios

Los flujos se diseñaron originalmente para texto, por lo que el modo de salida predeterminado es texto. En el modo de texto, el carácter de avance de línea (nueva línea) se expande a un par de retorno de carro y avance de línea. La expansión puede causar problemas, como se muestra aquí:

```cpp
// binary_output_files.cpp
// compile with: /EHsc
#include <fstream>
using namespace std;
int iarray[2] = { 99, 10 };
int main( )
{
    ofstream os( "test.dat" );
    os.write( (char *) iarray, sizeof( iarray ) );
}
```

Puede esperar que este programa envíe la secuencia de bytes { 99, 0, 10, 0 }; en su lugar, envía { 99, 0, 13, 10, 0 }, lo que provoca problemas para un programa que esperaba una entrada binaria. Si necesita una salida binaria verdadera, en la que los caracteres se escriben sin traducir, puede especificar una salida binaria mediante `openmode` el argumento del constructor de [InStream](../standard-library/basic-ofstream-class.md#basic_ofstream):

```cpp
// binary_output_files2.cpp
// compile with: /EHsc
#include <fstream>
using namespace std;
int iarray[2] = { 99, 10 };

int main()
{
   ofstream ofs ( "test.dat", ios_base::binary );

   // Exactly 8 bytes written
   ofs.write( (char*)&iarray[0], sizeof(int)*2 );
}
```

## <a name="see-also"></a>Vea también

[Flujos de salida](../standard-library/output-streams.md)
