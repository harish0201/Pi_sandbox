How to use the sandbox with seatbelt:

First create a function for bash/zsh with:
```
cat << 'EOF' >> ~/.bashrc

# Securely launch Pi Coding Agent inside Apple Seatbelt Sandbox
pi-safe() {
    local PROFILE_PATH="/Users/hkothand/ssh_folder/sandbox_pi/mindmap_owui/pi2.sb"

    if [ ! -f "$PROFILE_PATH" ]; then
        echo "Error: Seatbelt profile not found at $PROFILE_PATH"
        return 1
    fi

    echo "Launching Pi Agent in a secure macOS Seatbelt sandbox..."
    sandbox-exec -f "$PROFILE_PATH" -D WORKSPACE="$PWD" pi "$@"
}
source ~/.bashrc
# execute with:
pi-safe -p "List all .md files in current directory in 5seconds"
```

Put the settings.json in the ~/.pi/agent/ directory
