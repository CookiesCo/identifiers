
## `identifiers`

Specifications, models, and other utilities for working with proprietary identifiers at Cookies, including CTINs (_Cookies Trade Item Numbers_), IIDs (_Intacct Identifiers_), and more.


### Structure of this repo

Each key identifier in the Cookies universe has a corresponding Protocol Buffer definition file. In that file, a single proto model is typically defined, with any sub-models specified
within the scope of the specifying model. For example:

```proto
/**
 * Sample identifier definition.
 */

syntax = "proto3";

package cookies.identifiers;

import "cookies/identifiers/meta.proto";


// This is a sample identifier definition. It's expressed as a Protocol Buffer Message, with annotations on the model to define how it
// should be parsed and validated. The properties on the model represent the data values packed into the identifier, as applicable.
message SampleIdentifier {
    option (cookies.identifiers).identifier = {
        prefix: "ABC";
        chars { range { max: 5; } };
    }

    // Specifies the ID number generated for this sample identifier. Per spec (listed in the options above), the packed result of all
    // fields on this model cannot exceed 5 characters, and it should always begin with `ABC`.
    ExactNumericValue id_number = 1;
}
```

Using this code, parsing tools also hosted in this repo (or downstream) can:

1) Generate reliable parsing and validation logic
2) Express interpreted identifiers as models in applicable languages
3) Make use of these definitions within the scope of higher-order services


### Toolchain

The repo is built with Bazel, with each `.proto` defined in a `proto_library`. You can just `bazel build //:identifiers` to build the entire package.


---

🍪 Copyright © 2021, Cookies Creative Consulting & Promotions, Inc.

This repository contains private computer source code owned by Cookies (heretofore Cookies Creative Consulting & Promotions, a California Company). Use of this code in source or object form requires prior written permission from a duly-authorized member of Cookies Engineering. All rights reserved.
