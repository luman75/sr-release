#!/usr/bin/env bash


# id of the current commit
CURRNET_COMMIT=$(git rev-parse HEAD)

# name of the current tag if it points onto the current commit
CURRNET_TAG=$(git tag --points-at $CURRNET_COMMIT)

if [ "$CURRNET_TAG" == "" ]; then
    echo "To publish package you must run the process from tagged commit of pacakge repo."
else

    # we execute compiler on the current code
    npm publish
    ret_code=$?
    if [ $ret_code != 0 ]; then
      echo "Compilation has not succeed"
      exit $ret_code
    fi
fi