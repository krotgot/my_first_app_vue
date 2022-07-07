<template>
    <tr class="items-list__table-row">
        <td class="name">
            <input type="text">
        </td>
        <td class="qty">
            <input type="text">
        </td>
        <td class="price">
            <input type="text">
        </td>
        <td class="total">
            123
        </td>
    </tr>
</template>
<style lang="scss">
.items-list__table-row {
    margin: 15px 0;
    td {
        display: flex;
        flex-direction: column;
        justify-content: center;
        input {
            width: 100%;
            color: #fff;
            background-color: #1e2139;
            border: none;
            border-radius: 4px;
            padding: 12px 4px;

            &:focus,
            &:focus-visible {
                outline: none;
            }
        }
    }
}
</style>