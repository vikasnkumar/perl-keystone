# NAME

Keystone - Perl extension for keystone-engine

# SYNOPSIS

    use Keystone ':all';

    $ks = Keystone->new(KS_ARCH_X86, KS_MODE_64) || die "Can't init Keystone\n";
    @opcodes = $ks->asm("pop rax; inc rbx; ret", 0x040000a);

    foreach(@opcodes) {
      printf "0x%.2x ", $_;
    }
    print "\n";

# DESCRIPTION

This module is a Perl wrapper of the keystone-engine library.

Keystone is a lightweight multi-platform, multi-architecture assembler framework.

Further information are available at http://www.keystone-engine.org

## METHODS

- new(arch, mode)

        $ks = Keystone->new(KS_ARCH_X86, KS_MODE_32);

    Create a new keystone object.
    Take two arguments, the arch (KS\_ARCH\_\*) and the mode (KS\_MODE\_\*).
    See ks\_open() in keystone-engine documentation

- asm(code, address)

        @opcodes = $ks->asm("pop rax; ret", 0x080480bc);

    Assemble code, and return a list of opcodes.

    See ks\_asm() in keystone-engine documentation.

## EXAMPLES

    #!/usr/bin/perl

    use ExtUtils::testlib;
    use Keystone ':all';

    use strict;
    use warnings;

# SEE ALSO

http://keystone-engine.org/

https://github.com/t00sh/perl-keystone

# AUTHOR

Tosh, <tosh@t0x0sh.org>

# COPYRIGHT AND LICENSE

Copyright (C) 2016 by Tosh

This library is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.
