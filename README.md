# Mates

A very simple addressbook program. It was written as an experiment to learn
Rust, and it might contain hideous code. You're probably better off using one
of the
[alternatives](http://vdirsyncer.readthedocs.org/en/stable/supported.html#client-applications)
listed in vdirsyncer's documentation.

## Installation

You need to have Rust nightly and Cargo installed. Just run ``cargo build`` to
get a binary which only depends on a working ``grep`` command in your path.


## Usage

Run the binary with ``--help`` to list all environment variables that can be
used for configuration. ``MATES_INDEX`` and ``MATES_DIR`` must be set.

Before first usage and after each sync you need to recreate the index with
``mates index``.


# Integration

## Mutt

```
set query_command= "mates mutt-query '%s'"
bind editor <Tab> complete-query
bind editor ^T    complete
```

## Selecta

[selecta](https://github.com/garybernhardt/selecta), is a fuzzy text selector
that can be used instead of grep to search for contacts.

``
m() {
    mutt "$(MATES_GREP=selecta mates email-query)"
}
``

## Synchronization with CardDAV (and others)

[Vdirsyncer](http://vdirsyncer.readthedocs.org/) can be used to synchronize to
a CardDAV server. If you don't need that, using any decent file synchronization
will work too.

## License

mates is released under the public domain.
